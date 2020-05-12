---
title: python script scatter (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'scatter'

Functions in program: 
* `def scatterPlot(filename, sheet, X, Y, t, x_lb, y_lb):`

## python scatter

Python mysql example: scatter

```python
def scatterPlot(filename, sheet, X, Y, t, x_lb, y_lb):
    import matplotlib.pyplot as plt
    import numpy as np
    import helper
    import random
    import pandas as pd
    #from numpy.random import random
    import matplotlib.pylab as pylab
    
    # Valid font sizes are xx-small, x-small, small, medium, large, x-large, xx-large, smaller, larger
    
    params = {'legend.fontsize': 'xx-large',
              'figure.figsize': (20, 15),
             'axes.labelsize': 'xx-large',
             'axes.titlesize':'xx-large',
             'xtick.labelsize':'xx-large',
             'ytick.labelsize':'xx-large'}
    pylab.rcParams.update(params)

    
    
    df = pd.read_excel(filename, sheet_name = sheet)
    
    x = df[X]
    
    fig, ax = plt.subplots()
    #fig = plt.figure()
    
    colors = helper.colorsList(len(Y))
    markers = helper.uniqueMarkers(len(Y))
    
  
    for i, colName in enumerate(Y):
        y = df[colName]
        plt.scatter(x, y, marker = markers[i] , s=90, alpha=0.9, color=colors[i])
    
    
    plt.title(t)
    
    plt.legend(y_lb, loc='best', fontsize=12)
    
    # To make x ticks as strings instead of numbers
    #labels=['Frogs', 'Hogs', 'Bogs']
    #plt.xticks(x.values, labels, rotation='vertical')

    
    #fig.set_size_inches(18.5, 10.5)
    
    fig = ax.get_figure()
    
    ax.set_xlabel(x_lb, fontsize=20)
    #ax.set_ylabel(y_lb[0], fontsize=20)
    ax.set_ylabel('Number of Units Emitted', fontsize=20)
    

    rnd = [0,1, 2, 3]
    r = random.choice(rnd)
    if r == 0:
        #plt.grid()
        #ax.set_xticklabels(df[X], rotation=90)
        pass
    elif r == 1:
        plt.grid()
        #ax.set_xticklabels(df[X], rotation=90)
    elif r == 2:
        #plt.grid()
        ax.set_xticklabels(df[X], rotation=45)
    elif r == 3:
        plt.grid()
        ax.set_xticklabels(df[X], rotation=45) 
        
        
    ax.grid(zorder = 0)
    bool = [True, False]
    plt.grid(random.choice(bool))
    
    plt.title(t,fontsize = 20)
    plt.margins(0.1)
    plt.tight_layout
    
    #plt.show()
    
    path = 'plots/scatterPlots/co2_emission/'
        
    helper.make_sure_path_exists(path)
            
    figname = path + str(t) + '.png'
    fig.savefig(figname, dpi=100)

    
    
    path = 'plots/scatterPlots/co2_emission/'
    helper.make_sure_path_exists(path)
    
    figname = path + t + '.png'
    fig.savefig(figname, dpi=100)
    
    plt.clf()
    plt.cla()
    plt.close(fig)
    
    print('Scatter Plot is dumped at '+figname)
    
    return

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
