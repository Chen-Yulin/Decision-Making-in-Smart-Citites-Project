```python
from scipy.optimize import linprog
```


```python
links = [(1,2),(2,3),(3,4),(1,3),(2,4)]
capacities = {(1,2):6000, (2,3):6000, (3,4):6000, (1,3):3000, (2,4):3000}
travel_times = {(1,2):3, (2,3):3, (3,4):3, (1,3):10, (2,4):10}
```


```python
demands = {1:5000, 2:3000, 3:-5000, 4:-3000}
```


```python
c = [travel_times[link] for link in links]
```


```python
c
```




    [3, 3, 3, 10, 10]




```python
A_ub = []
b_ub = []
```


```python
# capacity constrain
for link in links:
    A_row = [int(link == l) for l in links]
    A_ub.append(A_row)
    b_ub.append(capacities[link])
    A_ub.append([-int(link == l) for l in links])
    b_ub.append(capacities[link])
```


```python
A_eq = []
b_eq = []
```


```python
# flow conservation
for node in [1,2,3]:
    A_row = [int(link[0] == node) - int(link[1] == node) for link in links]
    A_eq.append(A_row)
    if node not in demands:
        b_eq.append(0)
    else:
        b_eq.append(demands[node])  
```


```python
A_eq
```




    [[1, 0, 0, 1, 0], [-1, 1, 0, 0, 1], [0, -1, 1, -1, 0]]




```python
res = linprog(c=c, A_ub=A_ub, b_ub=b_ub, A_eq = A_eq, b_eq=b_eq)
```


```python
res.fun
```




    55999.9999531258




```python
res.x
```




    array([3866.70844779, 5999.99999497, 2133.29154718, 1133.29154802,
            866.70845031])




```python

```
