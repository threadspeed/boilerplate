---
title: python script simulate (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'simulate'

Functions in program: 
* `def main():`

Modules used in program: 
* `import random`
* `import argparse`

## python simulate

Python example: simulate

```python
#!/usr/bin/env python3.2

##################################################################
# Lim Jiew Meng (A0087884H)
# CS2106 OS Project 2 : Page Replacement Algorithms
##################################################################

import argparse
import random

# Abstract Base Class for Page Replacement Algorithm of a Virtual Memory
# to be used with class extending VirtualMemory
class PageReplacementAlgotithm:

    # called when a page request is found in memory (no page fault)
    # frames: the frame table
    # page: the page requested
    def hit(self, frames, page):
        pass

    # called when a page fault occurs
    # see hit() for info on params
    def miss(self, frames, page):
        pass
        
    # helper to find empty slot in frames
    # returns the index of an empty slot, -1 if no empty slot
    def emptySlot(self, frames):
        try: 
            index = frames.index(None)
            return index
        except BaseException:
            return -1
	

# VirtualMemory (VM) class. Page Replacement Algorithm is implemented 
# using the Strategy Pattern
#
# Basic workings: 
#
# get(page) queries the VM. It calls hit() or miss() in the 
# Page Replacement Stragety class. If its a miss, pageFaults is incremented. 
# Subclasses of PageRepacementAlgorithm should override the hit() or miss() 
# methods as approperiate (to implement the page replacement strategy)
class VirtualMemory:
    def __init__(self, numFrames, pageReplacementAlgorithm):
        # counter for page faults
        self.pageFaults = 0

        # frame table: M[f] -> p
        self.frames = [None] * numFrames

        # strategy to use for page replacement
        self.pageReplacementAlgorithm = pageReplacementAlgorithm

    # queries the frame table for the existance of a page
    # calls replacement algo hit() or miss() as applicable
    def get(self, page):
        if self.isPageFault(page):
            # call pageReplacementAlgorithm.miss()
            self.pageReplacementAlgorithm.miss(self.frames, page)
            
            # increment counter
            self.pageFaults += 1
        else: 
            self.pageReplacementAlgorithm.hit(self.frames, page)
        
        print("- LRU: " + str(self.pageReplacementAlgorithm.lru))
        print("- Frames: " + str(self.frames))
        
    # checks if a page is in the frame table (memory)
    def isPageFault(self, page):
        try:
            index = self.frames.index(page)
            return False
        except BaseException: # when page not found in frames (frame table)
            return True

class RandomPageReplacement(PageReplacementAlgotithm):

    # tries to fill an empty slot, otherwise pick a random slot to fill
    def miss(self, frames, page):
        index = self.emptySlot(frames)
        if index > -1:
            # fill empty slot
            frames[index] = page
        else: 
            # pick a random index (in frame table) to replace
            index = random.randint(0, len(frames) - 1)
            frames[index]
        
class FifoPageReplacement(PageReplacementAlgotithm):
    
    def __init__(self):
        self.first = 0;

    def miss(self, frames, page):
        index = self.emptySlot(frames)
        if index > -1:
            # fill empty slot
            frames[index] = page
        else: 
            # fill oldest frame
            frames[self.first] = page
            self.first = (self.first + 1) % len(frames)
        
class LruPageReplacement(PageReplacementAlgotithm):

    def __init__(self, numFrames):
        self.lru = [None] * numFrames
        self.numFrames = numFrames
    
    # moves page in lru to top
    def hit(self, frames, page):
        index = self.lru.index(page)
        del self.lru[index]
        self.lru.insert(0, page) 

    # always 
    def miss(self, frames, page):
        index = self.emptySlot(frames)
        if index > -1:
            # fill empty slot
            frames[index] = page
            
            # update lru
            del self.lru[self.numFrames - 1]
            self.lru.insert(0, page)
        else: 
            # Get the index of lru page in frame table
            leastRecentlyUsedPage = self.lru[self.numFrames - 1]
            leastRecentlyUsedPageIndex = frames.index(leastRecentlyUsedPage)
            
            # update frame table with new page
            frames[leastRecentlyUsedPageIndex] = page
            
            # update lru
            del self.lru[self.numFrames - 1]
            self.lru.insert(0, page)

    
    # helper to find the index of page in frames. -1 if not found
    def indexOf(self, frames, page):
        try:
            index = frames.index(page)
        except BaseException: 
            index = -1
        return index
        

def main():

    # parse arguments
    parser = argparse.ArgumentParser(description="Page Replacement Algorithm Simulator")
    parser.add_argument("references", metavar="RS", type=int, nargs="+", help="Reference string to use")
    parser.add_argument("--numFrames", metavar="F", type=int, default=1000, help="Number of frames in main memory")
    parser.add_argument("--numPages", metavar="P", type=int, default=100, help="Number of pages in virtual memory")

    args = vars(parser.parse_args())
    
    # do simulation
    vm = VirtualMemory(args['numFrames'], FifoPageReplacement())
    for r in args['references']:
        vm.get(r)

    # output results
    print("Number of page faults : " + str(vm.pageFaults))
	
main();

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
