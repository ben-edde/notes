# Network Flow

## Flow Network  

* a directed graph (V,E)  
* 1 source(s), 1 sink(t)
* each edge comes with capacity  
* only capacity, no flow  

## flow  

* a function (mapping)
* flow must be small than capacity
    > `0 <= f(each_edge) <=c(each_edge) for each_edge in E`
* flow conservation
    > sum of in-flow == sum of out-flow for all nodes excluding {s,t}

## net flow  
* flow from 1 node to another node  
    > f(a,b) 

## value of flow

* difference between sum of all net flow out of source and sum of all flow in to source  
    > [sum(f(s,v)) for v in s.out]-[sum(f(v,s)) for v in s.in]
* a valid quantity to flow through the network from source to sink  

## s-t cut  

* cut=partition(A,B)
* s is element of A
* t is element of B

## maximum flow problem

* maximize value of a flow  
* find a best arrangement of resource with respect to limited hardware

## Ford-Fulkerson

* greedy principle fails to yield optimal solution  
* need an algo that can adjust solutions by undoing some steps  
* keep augmenting flow until it is unavailable(no more augmenting path)


## residual network

## augment path

## Edmonds-Karp

## BFS

## maximum bipartile

pass