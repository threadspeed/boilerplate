---
title: python script TOMGRO (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'TOMGRO'

Functions in program: 
* `def validation(forests, teststartday, target):`
* `def machineL(traindata, target):`
* `def getTrain(train_startday):`
* `def TOMGRO(startday, get_period=1, step=1, trainmode=False):`
* `def validation(forests, teststartday, target):`
* `def machineL(traindata, target):`
* `def getTrain(train_startday):`
* `def TOMGRO(startday, get_period=1, step=1, trainmode=False):`
* `def averageInData(x, n):`
* `def splitOutData(y, n):`
* `def splitInData(x, n=24, step=1):`
* `def dayPlot(startday, y, title="", xlabel="", ylabel=""):`
* `def calcHour(startday, period):`
* `def calcDay(startday, period, hour=0):`
* `def pseudoClimate(filename, rng, fix=0):`
* `def calc(inT, inPPFD):`
* `def dWfdt(GRnet_, fF_, N, g_):`
* `def g(T_daytime):`
* `def fF(Td):`
* `def GRnet(Pg_, Rm_, fR_):`
* `def Rm(T, W, Wm):`
* `def Pg(LFmax_, PGRED_, PPFD, LAI):`
* `def PGRED(T):`
* `def LFmax(CO2):`
* `def fR(N):`
* `def dWmdt(Df_, Wf, Wm, N):`
* `def Df(T):`
* `def dWdt(LAI, dWfdt_, GRnet_, dens, dNdt_):`
* `def dLAIdt(LAI, dens, N, lambda_, dNdt_):`
* `def lambdas(Td):`
* `def dNdt(fN_):`
* `def fN(T):`

Modules used in program: 
* `import warnings`
* `import math`
* `import random as rnd`
* `import datetime`
* `import pandas as pd`
* `import random`
* `import matplotlib.animation as animation`
* `import matplotlib.pyplot as plt`
* `import numpy as np`

## python TOMGRO

Python example: TOMGRO

```python
#Reference
 #Jones(1999) "Reduced state-variable tomato growth model"
 #Jones(1991) "A dynamix tomato growth and yield model(TOMGRO)"
 #Dimokas(2009) "Calibration and validation of a biological model..."
 #Heuvelink(1994) "Dry-matter partitioning in a tomato crop:Comparison of two simulation models"

import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation
import random
from mpl_toolkits.mplot3d import Axes3D
from scipy.interpolate import griddata
import pandas as pd
from keras.utils import *
from keras.models import *
from keras.layers import *
from keras import regularizers
import datetime
import random as rnd
from sklearn import svm
from sklearn.metrics import r2_score
import math
from tqdm import tqdm

#Random Forest
from sklearn.ensemble import RandomForestRegressor

import warnings
warnings.filterwarnings("ignore")

##########
# dN/dt : The rate of node development
def fN(T):
  #Heuvelink(1994) & Jones(1991)
  if(T > 12 and T <= 28):
    return 1.0 + 0.0281 * (T - 28)
  elif(T > 28 and T < 50):
    return 1.0 - 0.0455 * (T - 28)
  else:
    return 0
  return 0

def dNdt(fN_):
  Nm = 0.5 #P Jones(1991)
  #("dNdt:", Nm * fN_)
  return Nm * fN_

##########
# d(LAI)/dt : The rate of LAI(Leaf Area Index) development

def lambdas(Td):
  return 1.0

def dLAIdt(LAI, dens, N, lambda_, dNdt_):
  sigma = 0.038 #P Maximum leaf area expansion per node, coefficient in expolinear equation; Jones(1999)
  beta = 0.169 #P Coefficient in expolinear equation; Jones(1999)
  Nb = 16.0 #P Coefficient in expolinear equation, projection of linear segment of LAI vs N to horizontal axis; Jones(1999)
  LAImax = 4.0 #P Jones(1999)

  if(LAI > LAImax):
    return 0
    
  a = np.exp(beta * (N - Nb))
  return dens * sigma * lambda_ * a * dNdt_ / (1 + a)

##########
# dW/dt
def dWdt(LAI, dWfdt_, GRnet_, dens, dNdt_):
  LAImax = 4.0 #P Jones(1999)
  if(LAI >= LAImax):
    p1 = 2.0 #P Jones(1999)
  else:
    p1 = 0
  Vmax = 8.0 #P Jones(1999)

  a = dWfdt_ + (Vmax - p1) * dens * dNdt_
  b = GRnet_ - p1 * dens * dNdt_
  return min(a, b)

# dWdt_max

##########
# dWmdt
def Df(T):
  # The rate of development or aging of fruit at temperature T; Jones(1991)
  if(T > 9 and T <= 28):
    return 0.0017 * T - 0.015
  elif(T > 28 and T <= 35):
    return 0.032
  else:
    return 0
  
def dWmdt(Df_, Wf, Wm, N):
  NFF = 22.0 #P Jones(1999)
  kF = 5.0 #P Jones(1999)

  if(N <= NFF + kF):
    return 0
  return Df_ * (Wf - Wm)

##########
# dWfdt : The rate of Fruit dry weight

def fR(N):
  #root phenology-dependent fraction; Jones(1991)
  if(N >= 30):
    return 0.07
  return -0.0046 * N + 0.2034

def LFmax(CO2):
  #maximum leaf photosyntehstic rate;Jones(1991)
  #CO2[ppm]?
  tau = 0.0693 #P carbon dioxide use efficiency; Jones(1991)
  return tau * CO2

def PGRED(T):
  #function to modify Pg under suboptimal daytime temperatures; Jones(1991)
  if(T > 0 and T <= 12):
    return 1.0 / 12.0 * T
  elif(T > 12 and T < 35):
    return 1.0
  else:
    return 0
  return 0

def Pg(LFmax_, PGRED_, PPFD, LAI):
  D = 2.593 #P coefficient to convert Pg from CO2 to CH2O; Jones(1991)
  K = 0.58 #P light extinction coefficient; Jones(1991)
  m = 0.1 #P leaf light transmission coefficient; Jones(1991)
  Qe = 0.0645 #P leaf quantum efficiency; Jones(1991)

  #if(PPFD > 250):
  #  PPFD = 0
  a = D * LFmax_ * PGRED_ / K
  b = np.log(((1-m) * LFmax_ + Qe * K * PPFD) / 
    ((1-m) * LFmax_ + Qe * K * PPFD * np.exp(-1 * K * LAI)))
  return  a * b

def Rm(T, W, Wm):
  #Jones(1999)
  #Hourly Data!
  Q10 = 1.4 #P Jones(1991)
  rm = 0.016 #P Jones(1999)
  return Q10 ** ((T-20)/10) * rm * (W - Wm)

def GRnet(Pg_, Rm_, fR_):
  E = 0.717 #P convert efficiency; Dimokas(2009)
  #print("GRnet", Pg_, Rm_, fR_)
  return max(0, E * (Pg_ - Rm_) * (1 - fR_))

def fF(Td):
  #Jones(1991)
  if(Td > 8 and Td <= 28):
    return 0.0017 * Td - 0.0147
  elif(Td > 28):
    return 0.032
  else:
    return 0
  return 0

def g(T_daytime):
  T_CRIT = 24.4 #P mean daytime temperature above which fruits abortion start; Jones(1999)
  if(T_daytime < T_CRIT):
    return 0
  return 1.0 - 0.154 * (T_daytime - T_CRIT)

def dWfdt(GRnet_, fF_, N, g_):
  NFF = 22.0 #P Nodes per plant when first fruit appears; Jones(1999)
  alpha_F = 0.80 #P Maximum partitioning of new growth to fruit; Jones(1999)
  v = 0.135 #P Transition coefficient between vegetative and full fruit growth; Jones(1999)
  fF_ = 0.5 #P ORIGINAL
  if(N <= NFF):
    return 0
  #print(GRnet_, fF_, 1 - np.exp(v*(NFF-N)), g_)
  return GRnet_ * alpha_F * fF_ * (1 - np.exp(v*(NFF-N))) * g_

def calc(inT, inPPFD):
  # Initial Variables
  N = 6.0
  LAI = 0.006
  W = 0
  Wm = 0
  Wf = 0
  CO2 = 350

  # Growth data per day
  N_hist = []
  LAI_hist = []
  W_hist = []
  Wm_hist = []
  Wf_hist = []

  # Growth rate per day
  delN = []
  delLAI = []
  delW = []
  delWm = []
  delWf = []

  length = int(len(inT)/24)*24

  for i in range(0, length, 24):
    # Reset varialbes
    dNdt_ = 0
    Td = 0 # Change!
    Tdaytime = 0
    PPFDd = 0

    # for daily tempereture
    for h in range(24):
      Td += inT[i+h]
      PPFDd += inPPFD[i+h]
      if(h==13): #14時
        Tdaytime = inT[i+h]
    Td /= 24 # average dialy temperature
    PPFDd /= 24 # average dialy temperature
    fN_ = fN(Td)
    dNdt_ += dNdt(fN_)

    # dN/dt
    #fN_ = fN(Td)
    #dNdt_ += dNdt(fN_)

    # d(LAI)/dt
    lambda_ = lambdas(Td)
    dLAIdt_ = dLAIdt(LAI=LAI, dens=3.10, N=N, lambda_=lambda_, dNdt_=dNdt_)

    # dWfdt
    fR_ = fR(N)
    LFmax_ = LFmax(CO2)
    PGRED_ = PGRED(Td)
    Pg_ = Pg(LFmax_, PGRED_, PPFDd, LAI)
    Rm_ = Rm(Td, W, Wm)
    GRnet_ = GRnet(Pg_, Rm_, fR_)
    fF_ = fF(Td)
    g_ = g(Tdaytime)
    dWfdt_ = dWfdt(GRnet_, fF_, N, g_)

    # dWdt
    dWdt_ = dWdt(LAI=LAI, dWfdt_=dWfdt_, GRnet_=GRnet_, dens=3.10, dNdt_=dNdt_)

    # dWmdt
    Df_ = Df(Td)
    dWmdt_ = dWmdt(Df_, Wf, Wm, N)

    # Reload
    N += dNdt_
    LAI += dLAIdt_
    Wf += dWfdt_
    W += dWdt_
    Wm += dWmdt_

    # Save
    N_hist.append(N)
    LAI_hist.append(LAI)
    W_hist.append(W)
    Wf_hist.append(Wf)
    Wm_hist.append(Wm)
    delN.append(dNdt_)
    delLAI.append(dLAIdt_)
    delW.append(dWdt_)
    delWf.append(dWfdt_)
    delWm.append(dWmdt_)

  N_hist = np.array(N_hist)
  LAI_hist = np.array(LAI_hist)
  W_hist = np.array(W_hist)
  Wf_hist = np.array(Wf_hist)
  Wm_hist = np.array(Wm_hist)
  delN = np.array(delN)
  delLAI = np.array(delLAI)
  delW = np.array(delW)
  delWf = np.array(delWf)
  delWm = np.array(delWm)

  # X:Final Value, X_hist:Values per Day, delX:Growth Rate per Day
  return {"N":N, "LAI":LAI, "Wf":Wf, "W":W, "Wm":Wm,
          "N_hist":N_hist, "LAI_hist":LAI_hist,"W_hist":W_hist,"Wf_hist":Wf_hist,"Wm_hist":Wm_hist,
          "delN":delN, "delLAI":delLAI, "delWf":delWf, "delW":delW, "delWm":delWm}

def pseudoClimate(filename, rng, fix=0):
  df = pd.read_csv(filename, sep=',', index_col='date')
  data_range = pd.date_range('2018-08-20 01:00:00',periods=rng,freq='d')

  """
  #グラフ表示
  data_range = pd.date_range('2019-03-20 01:00:00',periods=5160,freq='H')
  plt.plot(data_range, df['temperature'])
  plt.show()
  plt.plot(data_range, df['PPFD'])
  plt.show()
  """

  #print(df['temperature'])
  return {'date':data_range, 'T':df['temperature'], 'PPFD':df['PPFD']}

def calcDay(startday, period, hour=0):
  date_formatted = datetime.datetime.strptime(startday, "%Y/%m/%d %H:%M")
  after = date_formatted + datetime.timedelta(days=period) + datetime.timedelta(hours=hour)
  return after.strftime("%Y/%-m/%-d %-H:%M")

def calcHour(startday, period):
  date_formatted = datetime.datetime.strptime(startday, "%Y/%m/%d %H:%M")
  after = date_formatted + datetime.timedelta(hours=period)
  return after.strftime("%Y/%-m/%-d %-H:%M")

def dayPlot(startday, y, title="", xlabel="", ylabel=""):
  data_range = pd.date_range(startday, periods=len(y), freq='d')
  plt.rcParams["font.size"] = 12
  plt.xticks(rotation=90)
  if(title!=""):
    plt.title(title, fontsize=18)
  if(xlabel!=""):
    plt.xlabel(xlabel, fontsize=18)
  if(ylabel!=""):
    plt.ylabel(ylabel, fontsize=18)
  plt.plot(data_range, y)
  plt.show()

def splitInData(x, n=24, step=1):
  # x:Input data n:1つの成長率に対応する元々の入力データ数[時間] step:平均間隔
  resX, tmpX = np.empty(0), np.empty(0)
  for i in range(0, len(x)-n+1, n):
    xx = x[i:i+n]
    for j in range(0, n-step+1, step):
      tmpX = np.append(tmpX, np.average(xx[j:j+step]))
    resX = np.append(resX, tmpX)
    tmpX = np.empty(0)
    #print(resX.shape)
  resX = resX.reshape(-1, int(n/step))

  return resX

def splitOutData(y, n):
  resY = np.empty(0)
  for i in range(len(y)-1):
    deltaY = y[i+1] - y[i]
    resY = np.append(resY, deltaY)
  return resY

def averageInData(x, n):
  """
  #夜、日中の平均
  resX = np.empty(0)
  daytime, night = 0, 0
  for i in range(0, len(x)-n, 24):
    daytime = np.average(x[i+6:i+19])
    night = np.average(x[i+0:i+6]) + np.average(x[i+19:i+24])
    resX = np.append(resX, np.array([daytime, night/2]))
  return resX.reshape(-1 , 2)
  """
  resX = np.empty(0)
  for i in range(0, len(x)-n, 24):
    average = np.average(x[i:24+i])
    resX = np.append(resX, average)
  return resX

def TOMGRO(startday, get_period=1, step=1, trainmode=False):
# startday:定植時刻 get_period:最終定植時刻数 step:定植時刻間隔 

  splitPeriod = 24 # hour
  ave_step = 3
  get_period = int(get_period/step)

  datas = pseudoClimate('./weather_Tokyo.csv', 400)
  T = datas['T']
  PPFD = datas['PPFD']
  xT, xP = np.empty(0), np.empty(0)
  delN, delLAI, delW, delWf, delWm = np.empty(0), np.empty(0), np.empty(0), np.empty(0), np.empty(0)
  N_hist, LAI_hist, W_hist, Wf_hist, Wm_hist = np.empty(0), np.empty(0), np.empty(0), np.empty(0), np.empty(0)

  for i in tqdm(range(0,get_period,step)):
    endday = calcDay(startday, period=100)
    inT = np.array(T[startday:endday].tolist()) # ある日の1:00～99日後の1:00
    inP = np.array(PPFD[startday:endday].tolist())
    startday = calcHour(startday, period=step)
    res = calc(inT, inP)
    delN = np.append(delN, res['delN'])
    delLAI = np.append(delLAI, res['delLAI'])
    delW = np.append(delW, res['delW'])
    delWf = np.append(delWf, res['delWf'])
    delWm = np.append(delWm, res['delWm'])
    N_hist = np.append(N_hist, res['N_hist'])
    LAI_hist = np.append(LAI_hist, res['LAI_hist'])
    W_hist = np.append(W_hist, res['W_hist'])
    Wf_hist = np.append(Wf_hist, res['Wf_hist'])
    Wm_hist = np.append(Wm_hist, res['Wm_hist'])

    if(i>0):
      xT = np.concatenate([xT, splitInData(inT, splitPeriod, step=ave_step)])
      xP = np.concatenate([xP, splitInData(inP, splitPeriod, step=ave_step)])
    else:
      xT = splitInData(inT, splitPeriod, step=ave_step)
      xP = splitInData(inP, splitPeriod, step=ave_step)
  x = np.concatenate([xT, xP], axis=1)
  if(trainmode):
    x = np.insert(x, 0, Wm_hist, axis=1)
    x = np.insert(x, 0, Wf_hist, axis=1)
    x = np.insert(x, 0, W_hist, axis=1)
    x = np.insert(x, 0, LAI_hist, axis=1)
    x = np.insert(x, 0, N_hist, axis=1)
    
  print(x.shape)
  print(delN.shape)

  return {'x':x, 'xT':xT, 'xP':xP,
          'delN':delN, 'delLAI':delLAI, 'delW':delW, 'delWf':delWf, 'delWm':delWm,
          'N_hist':N_hist, 'LAI_hist':LAI_hist, 'W_hist':W_hist, 'Wf_hist':Wf_hist, 'Wm_hist':Wm_hist}

def getTrain(train_startday):
  step = 6 #[hour]
  period = 365 * 1 * 24
  traindata = TOMGRO(train_startday, get_period=period, step=step, trainmode=True) #get_period, step [hour]
  return traindata

def machineL(traindata, target):
  xT, xP = traindata['xT'], traindata['xP']
  delY = traindata[target]
  N_hist, LAI_hist, W_hist, Wf_hist, Wm_hist = traindata['N_hist'], traindata['LAI_hist'], traindata['W_hist'],  traindata['Wf_hist'],  traindata['Wm_hist']
  x = traindata['x']
  y = delY

  #モデル
  forest = RandomForestRegressor(n_estimators=20)
  forest.fit(x, y)

  return forest

def validation(forests, teststartday, target):
  #評価
  id = 3
  testdata = TOMGRO(teststartday)
  x = testdata['x']
  delY = testdata[target]
  addx = np.array([6.0, 0.0, 0.0, 0.0, 0.0])
  p, y = addx[id], addx[id] #CHANGE
  P, Y = np.empty(0), np.empty(0)
  i = 0
  for eachx in x:
    eachx = np.append(addx, eachx)
    newaddx = np.empty(0)
    for forest in forests:
      newaddx = np.append(newaddx, forest.predict(eachx.reshape(1,-1)))
    addx += newaddx
    p = p + newaddx[id] #CHANGE
    y = y + delY[i]
    i = i + 1
    P = np.append(P, p)
    Y = np.append(Y, y)

  dayPlot(teststartday, Y, xlabel="day", ylabel="TOMGRO")
  dayPlot(teststartday, P, xlabel="day", ylabel="Predicted")
  dayPlot(teststartday, np.abs(Y-P)/Y, xlabel="day", ylabel="DELTA")

  """
  plt.scatter(delY, predicted, alpha=0.3)
  plt.xlabel("TOMGRO")
  plt.ylabel("Predicted")
  plt.show()
  """

  #相関係数
  #return np.dot(predicted, delY)/(np.linalg.norm(predicted, ord=2)*np.linalg.norm(delY, ord=2))
  return 0

#TOMGRO
train_startday = "2016/1/1 1:00"
test_startday = "2018/5/1 1:00"

#MachineLearning
#traindata = getTrain(train_startday)
forestN = machineL(traindata, 'delN')
forestLAI = machineL(traindata, 'delLAI')
forestW = machineL(traindata, 'delW')
forestWf = machineL(traindata, 'delWf')
forestWm = machineL(traindata, 'delWm')
forests = [forestN, forestLAI, forestW, forestWf,forestWm]
r = validation(forests, test_startday, 'delWf')
print(r)
  sumP = np.empty(0)
  for i in range(p.shape[0]):
    sumP = np.append(sumP, np.sum(p[0:i]))
  return sumP

#Random Forest
from sklearn.ensemble import RandomForestRegressor

def TOMGRO(startday, get_period=1, step=1, trainmode=False):
# startday:定植時刻 get_period:最終定植時刻数 step:定植時刻間隔 

  splitPeriod = 24 # hour
  ave_step = 3
  get_period = int(get_period/step)

  datas = pseudoClimate('./weather_Tokyo.csv', 400)
  T = datas['T']
  PPFD = datas['PPFD']
  xT, xP = np.empty(0), np.empty(0)
  delN, delLAI, delW, delWf, delWm = np.empty(0), np.empty(0), np.empty(0), np.empty(0), np.empty(0)
  N_hist, LAI_hist, W_hist, Wf_hist, Wm_hist = np.empty(0), np.empty(0), np.empty(0), np.empty(0), np.empty(0)

  for i in tqdm(range(0,get_period,step)):
    endday = calcDay(startday, period=100)
    inT = np.array(T[startday:endday].tolist()) # ある日の1:00～99日後の1:00
    inP = np.array(PPFD[startday:endday].tolist())
    startday = calcHour(startday, period=step)
    res = calc(inT, inP)
    delN = np.append(delN, res['delN'])
    delLAI = np.append(delLAI, res['delLAI'])
    delW = np.append(delW, res['delW'])
    delWf = np.append(delWf, res['delWf'])
    delWm = np.append(delWm, res['delWm'])
    N_hist = np.append(N_hist, res['N_hist'])
    LAI_hist = np.append(LAI_hist, res['LAI_hist'])
    W_hist = np.append(W_hist, res['W_hist'])
    Wf_hist = np.append(Wf_hist, res['Wf_hist'])
    Wm_hist = np.append(Wm_hist, res['Wm_hist'])

    if(i>0):
      xT = np.concatenate([xT, splitInData(inT, splitPeriod, step=ave_step)])
      xP = np.concatenate([xP, splitInData(inP, splitPeriod, step=ave_step)])
    else:
      xT = splitInData(inT, splitPeriod, step=ave_step)
      xP = splitInData(inP, splitPeriod, step=ave_step)
  x = np.concatenate([xT, xP], axis=1)
  if(trainmode):
    x = np.insert(x, 0, Wm_hist, axis=1)
    x = np.insert(x, 0, Wf_hist, axis=1)
    x = np.insert(x, 0, W_hist, axis=1)
    x = np.insert(x, 0, LAI_hist, axis=1)
    x = np.insert(x, 0, N_hist, axis=1)
    
  print(x.shape)
  print(delN.shape)

  return {'x':x, 'xT':xT, 'xP':xP,
          'delN':delN, 'delLAI':delLAI, 'delW':delW, 'delWf':delWf, 'delWm':delWm,
          'N_hist':N_hist, 'LAI_hist':LAI_hist, 'W_hist':W_hist, 'Wf_hist':Wf_hist, 'Wm_hist':Wm_hist}

def getTrain(train_startday):
  step = 6 #[hour]
  period = 365 * 1 * 24
  traindata = TOMGRO(train_startday, get_period=period, step=step, trainmode=True) #get_period, step [hour]
  return traindata

def machineL(traindata, target):
  xT, xP = traindata['xT'], traindata['xP']
  delY = traindata[target]
  N_hist, LAI_hist, W_hist, Wf_hist, Wm_hist = traindata['N_hist'], traindata['LAI_hist'], traindata['W_hist'],  traindata['Wf_hist'],  traindata['Wm_hist']
  x = traindata['x']
  y = delY

  #モデル
  forest = RandomForestRegressor(n_estimators=20)
  forest.fit(x, y)

  return forest

def validation(forests, teststartday, target):
  #評価
  id = 3
  testdata = TOMGRO(teststartday)
  x = testdata['x']
  delY = testdata[target]
  addx = np.array([6.0, 0.0, 0.0, 0.0, 0.0])
  p, y = addx[id], addx[id] #CHANGE
  P, Y = np.empty(0), np.empty(0)
  i = 0
  for eachx in x:
    eachx = np.append(addx, eachx)
    newaddx = np.empty(0)
    for forest in forests:
      newaddx = np.append(newaddx, forest.predict(eachx.reshape(1,-1)))
    addx += newaddx
    p = p + newaddx[id] #CHANGE
    y = y + delY[i]
    i = i + 1
    P = np.append(P, p)
    Y = np.append(Y, y)

  dayPlot(teststartday, Y, xlabel="day", ylabel="TOMGRO")
  dayPlot(teststartday, P, xlabel="day", ylabel="Predicted")
  dayPlot(teststartday, np.abs(Y-P)/Y, xlabel="day", ylabel="DELTA")

  """
  plt.scatter(delY, predicted, alpha=0.3)
  plt.xlabel("TOMGRO")
  plt.ylabel("Predicted")
  plt.show()
  """

  #相関係数
  #return np.dot(predicted, delY)/(np.linalg.norm(predicted, ord=2)*np.linalg.norm(delY, ord=2))
  return 0

#TOMGRO
train_startday = "2016/1/1 1:00"
test_startday = "2018/5/1 1:00"

#MachineLearning
#traindata = getTrain(train_startday)
forestN = machineL(traindata, 'delN')
forestLAI = machineL(traindata, 'delLAI')
forestW = machineL(traindata, 'delW')
forestWf = machineL(traindata, 'delWf')
forestWm = machineL(traindata, 'delWm')
forests = [forestN, forestLAI, forestW, forestWf,forestWm]
r = validation(forests, test_startday, 'delWf')
print(r)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
