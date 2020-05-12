---
title: python script igraph2NoroSonia (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'igraph2NoroSonia'

Functions in program: 
* `def main():`

Modules used in program: 
* `import sys, getopt`

## python igraph2NoroSonia

Python example: igraph2NoroSonia

```python
#a simple network-based SIR model written in Python
#Jon Zelner
#University of Michigan
#August 11, 2009
import sys, getopt
from igraph2Sonia import igraph2sonia

#for networks
def main():
    def usage():
        
        print("\n\nA simple model of an SIR epidemic on a small-world lattice")
        print("Takes the following options:")
        print("-b [beta]; transmission rate")
        print("-g [gamma]; average recovery rate")
        print("-N number of individuals")
        print("-p probability of edge rewiring")
        print("--np; suppress time series plotting")
        print("--nei; number of network neighbors")
        print("to run, ex:")
        print("   python networkSIR.py -b .02 -g .01\n\n")
        
    try:
        import igraph
    except ImportError:
        raise("You must have igraph installed to use this model!")
    
    #for random numbers
    try: 
        import scipy
        from scipy import random
    except:
        import random
        assert ("Python built-in RNGs aren't stable; please install Scipy for experimental output.")
    
        
    
    #what it sounds like; for making copies of objects
    import copy
    
    #for plotting
    makeTSPlot = True
    try:
        import pylab as pl
    except ImportError:
        makeTSPlot = False
        
    #for grabbing command line arguments and doing other 'sys'temsy things
    import sys
    
    #check to see if there are command-line arguments; if so bring them in
    
    try:  
        opts, args = getopt.getopt(sys.argv[1:], "b:B:g:G:n:N:p:P:h", ["np", "nei:"])
    except getopt.GetoptError, err:
        print(str(err))
        sys.exit(2)

    b = .11
    g = .1 
    N = 500
    p = 0.05
    neighbors = 2
    
    for o,a in opts:
        if o == "-b":
            b = float(a)
        elif o == "-g":
            g = float(a)
        elif o in ("-N", "-n"):
            N = int(a)
        elif o in ("-p", "-P"):
            p = float(a)
        elif o == "--nei":
            print(a) 
            neighbors = int(a)
        elif o == "--np":
            makeTSPlot = False
        elif o == '-h':
            usage()
            sys.exit(2)
            
    t = 0
    
    #generate a small-world network
    graph = igraph.Graph.Watts_Strogatz(1, N, nei=neighbors, p = p)
    
    #this gets rid of multiple edges and self-loops
    graph.simplify()
    
    #now we're going to start tracking connections between individuals. Entries are indexed by individual id. 
    #At each index is a list with that individual's connections
    adjacencyList = []
    for i in range(N):
        adjacencyList.append([])
    
    #just telling connections about each other
    for edge in graph.es:
        adjacencyList[edge.source].append(edge.target)
        adjacencyList[edge.target].append(edge.source)
    
    #these hold the IDs of individuals in each of the three states
    sAgentList = []
    iAgentList = []
    rAgentList = []
    infectionTimes = {}
    recoveryTimes = {}
    
    #these are for holding counts of the number of individuals in each state
    sList = []
    iList = []
    rList = []
    newIList = []
    
    #make a list of IDs
    allAgents = range(N)
    
    #shuffle the list so we grab individuals in no particular order
    random.shuffle(allAgents)
    
    #we start out with everyone susceptible
    sAgentList = copy.copy(allAgents)
    
    #take one individual and make them infectious - this is our 'index case'
    indexCase = sAgentList.pop()
    iAgentList.append(indexCase)
    
    #as long as we have infectious individuals, keep looping
    while len(iAgentList) > 0:
        #here, we keep track of who is going to be infected at the *end* of the step and who will recover
        tempIAgentList = []
        recoverList = []
        newI = 0
        
        #just look through the list of infected individuals instead of looking @ everyone
        for iAgent in iAgentList:
            #look in that individual's adjacency list
            for agent in adjacencyList[iAgent]:
                #is that agent susceptible?
                if agent in sAgentList:
                    #if so, try to infect
                    if (random.random() < b):
                        #if we infect, we can immediately take them off of the susceptible list
                        sAgentList.remove(agent)
                        #but don't add them to the infectious list yet
                        tempIAgentList.append(agent)
                        infectionTimes[agent] = t
                        newI += 1
                        
            #figure out if agent will recover @ end of step
            if (random.random() < g):
                recoverList.append(iAgent)
                recoveryTimes[iAgent] = t
        
        #now recover agents and remove them from the infectious list
        for recoverAgent in recoverList:
            iAgentList.remove(recoverAgent)
            rAgentList.append(recoverAgent)
        
        #and add newly infected agents to the infectious agent list
        iAgentList.extend(tempIAgentList)
        
        #here, we keep track of how many individuals are in each state
        sList.append(len(sAgentList))
        iList.append(len(iAgentList))
        rList.append(len(sAgentList))
        newIList.append(newI)
        t += 1
    
    graphList = {}
    for v in graph.vs():
        v['label_size'] = 0
        v['color'] = 'blue'
        v['size'] = 5
        if v.index == indexCase or infectionTimes.has_key(v.index):            
            if v.index == indexCase:
                v['time'] = 0
                v['iTime'] = 0
                v['color'] = 'green'
                graphList[indexCase] = 0
            else:
                v['iTime'] = infectionTimes[v.index]
                v['color'] = 'red'
            try:
                v['rTime'] = recoveryTimes[v.index]
            except:
                pass
            
            for nei in graph.neighbors(v.index):
                if not graphList.has_key(nei):
                    graph.vs[nei]['time'] = v['iTime']+2
                    graphList[nei] = graph.vs[nei]['time']+2
                elif graphList[nei] > v['iTime']+1:
                    graph.vs[nei]['time'] = v['iTime']+2
                    graphList[nei] = graph.vs[nei]['time']+2
                else:
                    pass
        else:
            v['time'] = t+1
        
    
    #l = graph.layout_circle()
    l = graph.layout_kamada_kawai()
    #l = graph.layout_grid_fruchterman_reingold()
    igraph.drawing.plot(graph, layout = l)
    
    if makeTSPlot:
        pl.figure()
        pl.plot(iList)
        pl.show()
    
    igraph2sonia(graph, "/Users/jzelner/Desktop/testMovie.son")
    

    
if __name__ == "__main__":
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
