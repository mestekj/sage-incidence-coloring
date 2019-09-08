# About

This project is an Python (with the use of SageMath) implementation of algorithms for incidence coloring of graphs of maximum degree 3 and 4.
The algorithms are described in [1] (graphs of maximum degree 3) and [2] (graphs of maximum degree 4).

# Getting started

## Instalation

### Prerequisities
The implementation uses [SageMath](http://www.sagemath.org) therefore it is neccessary to have it installed.
Any standard instalation (e.g. using [downloaded binary installer](http://www.sagemath.org/download.html)) is fine, 
there is no need to compile any custom version from source code.

### Usage in Sage Notebook
Firstly, copy files `incidence_coloring.py` and `incidence_coloring_degree3.py` to the same folder where your notebook (.ipynb file) is.
Then in notebook cell use `load('incidence_coloring.py')` to load the modules.


## API

Module `incidence_coloring.py` provides function `incidence_coloring(G, hex_colors)` where `G` is an undirected graph and 
``hex_colors`` is a boolean parameter. 

If `hex_colors` is `false`, created coloring will use colors _{1,2,3,4,5}_ for graphs of maximum degree 3, resp. _{1,2,3,4,5,6,7}_ for graphs of maximum degree 4. 
If `hex_colors` is `true` it will use RGB colors (as hexadecimal number) that are perfect for plotting the graph.

The returned incidence coloring is dictionary which keys are colors and values are lists of incidences colored with the color.
An incidence _(v,e)_ where _e_ is an edge _uv_ is represented by tuple `(v,u)`, i.e. incidences are viewed as directed edges. 

## Examples

Input (code in Notebook cell):
```python
load('incidence_coloring.py')
G = graphs.CycleGraph(5)
print incidence_coloring(G,false)
```

Output:
```
{1: [], 2: [(1, 2), (4, 0)], 3: [(3, 2), (0, 4)], 4: [(2, 3), (1, 0), (4, 3)], 5: [(2, 1), (3, 4), (0, 1)]}
```

### Visualise the coloring

Input (code in Notebook cell):
```python
load('incidence_coloring.py')
G = graphs.CycleGraph(5)
G.show()
C = incidence_coloring(G,true)
(G.to_directed()).plot(edge_colors=C)
```

Output:
*plotted graph*

### More examples
The file `IncidenceColoring.ipynb` is Sage Notebook containing examples of use of implemented functions.

# References
1. M. Maydanskiy. The incidence coloring conjecture for graphs of maximum degree three. *Discrete Math.* 292:131-141 (2005). [doi:10.1016/j.disc.2005.02.003](http://dx.doi.org/10.1016/j.disc.2005.02.003)
2. P. Gregor, B. Lužar, R. Soták. Note on incidence chromatic number of subquartic graphs. *J. Comb. Optim.* (2016). [doi:0.1007/s10878-016-0072-2](http://dx.doi.org/10.1007/s10878-016-0072-2)
