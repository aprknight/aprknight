from timeit import timeit

coordinates = ('S', 'W', 'W', 'S', 'E', 'S', 'E', 'N', 'N')

def func1(): # simplistic single pass
    sn = []
    ew = []

    for c in coordinates:
        if c in 'SN':
            sn.append(c)
        else:
            ew.append(c)
    
    return tuple(sn), tuple(ew)

def func2(): # tuple
    NS = ('N','S')
    EW = ('E','W')
    sn = [s for s in coordinates if s in NS]
    ew = [s for s in coordinates if s in EW]
    return tuple(sn), tuple(ew)

def func3(): # string
    NS = 'NS'
    EW = 'EW'
    sn = [s for s in coordinates if s in NS]
    ew = [s for s in coordinates if s in EW]
    return tuple(sn), tuple(ew)

def func4(): # set
    NS = {'N','S'}
    EW = {'E','W'}
    sn = [s for s in coordinates if s in NS]
    ew = [s for s in coordinates if s in EW]
    return tuple(sn), tuple(ew)

def func5(): # list
    NS = ['N','S']
    EW = ['E','W']
    sn = [s for s in coordinates if s in NS]
    ew = [s for s in coordinates if s in EW]
    return tuple(sn), tuple(ew)

for func in func1, func2, func3, func4, func5:
    print(func.__name__, timeit(lambda:func()))
