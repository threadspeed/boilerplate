---
title: python script multiline scatter (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'multiline scatter'

Functions in program: 
* `def scatterPlot_multi(file_list, sheet_list, X, Y_list,x_lb, y_lb, title, dirname,it):`

## python multiline scatter

Python example: multiline scatter

```python
def scatterPlot_multi(file_list, sheet_list, X, Y_list,x_lb, y_lb, title, dirname,it):
    import matplotlib.pyplot as plt
    import numpy as np
    import assistant as helper
    import random
    import pandas as pd
    #from numpy.random import random
    import matplotlib.pylab as pylab
    import gc
    
    t = title
    
    # Valid font sizes are xx-small, x-small, small, medium, large, x-large, xx-large, smaller, larger
    
    params = {'legend.fontsize': 'xx-large',
              'figure.figsize': (20, 15),
             'axes.labelsize': 'xx-large',
             'axes.titlesize':'xx-large',
             'xtick.labelsize':'xx-large',
             'ytick.labelsize':'xx-large'}
    pylab.rcParams.update(params)
       
    colors = helper.colorsList(29)
    markers = helper.uniqueMarkers(15)
    style = helper.linestylelist(3)
    
    import ntpath
    columns=[]
    for each in file_list:
        c = ntpath.basename(each).split('.')[0]
        columns.append('Opening Price of Company '+c)
    
    tmp = pd.DataFrame(columns = columns)

    for p,file in enumerate(file_list):
        df = pd.read_excel(file, sheet_name = sheet_list[p])
        if p==0:
            import random
            r = random.randint(0, len(df)-40)
        
        tmp[columns[p]] = df[Y_list[p]][r:r+40]
    toss = [0,1]
    tmp['Date'] = df['Date']
    tmp.set_index('Date')
    #ax = tmp.plot(x='Date', y=columns[0: len(columns)],style=['*', 'o', 'v'],fontsize=12)
    #ax = tmp.plot(x='Date', y=columns[0: len(columns)],fontsize=12,color=colors,linewidth = 3)
    ax = tmp.plot(x='Date', y=columns[0: len(columns)],fontsize=12,color=colors,linewidth = 3,marker=helper.uniqueMarkers(15)[random.choice(toss)], markersize=12.5)
    
    
    #
    fig = ax.get_figure()

    #*************************************************************************
#     SET X and Y AXIS LABELS
    ax.set_xlabel(x_lb, fontsize=20)
    ax.set_ylabel(y_lb, fontsize=20)

    rot = [90,45]
    ax.set_xticks(range(0, len(tmp)))
    ax.set_xticklabels(range(0, len(tmp)))

    plt.minorticks_on()

    #*************************************************************************
    # GRID ON/OFF RANDOMLY
    #ax.grid(zorder = 0)
    bool = [True, False]
    plt.grid(random.choice(bool))
    #ax.grid(True)

    #*************************************************************************
    # TITLE OF THE PLOT
    plt.title(title,fontsize = 20)


    #*************************************************************************
    # LEGENDS
    plt.legend(loc='best')

    #
    plt.show()

    #*************************************************************************
    # SAVE THE FIGURE
    path = 'plots/' + dirname + '/' + 'scatter' + '/'
    helper.make_sure_path_exists(path)            
    figname = path + str(title) + str(it) + '.png'
    fig.savefig(figname, dpi=100, bbox_inches = 'tight')
    print('Figure dumped at ' + figname)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
