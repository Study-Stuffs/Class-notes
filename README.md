**Importants:**
![topics](https://cdn.discordapp.com/attachments/915830242692718633/1089522073283596408/image.png)

## Quick Sort:
**Pseudocode for quick sort:**
    
        quicksort(A, p, r)
            if p < r
                q = partition(A, p, r)
                quicksort(A, p, q-1)
                quicksort(A, q+1, r)
    
        partition(A, p, r)
            x = A[r]
            i = p-1
            for j = p to r-1
                if A[j] <= x
                    i = i+1
                    exchange A[i] with A[j]
            exchange A[i+1] with A[r]
            return i+1
* **Average Case:** O(nlogn)
* **Worst Case:** O(n^2)

## Merge Sort:
**Pseudocode for merge sort:**

        mergesort(A, p, r)
            if p < r
                q = (p+r)/2
                mergesort(A, p, q)
                mergesort(A, q+1, r)
                merge(A, p, q, r)
    
        merge(A, p, q, r)
            n1 = q-p+1
            n2 = r-q
            let L[1..n1+1] and R[1..n2+1] be new arrays
            for i = 1 to n1
                L[i] = A[p+i-1]
            for j = 1 to n2
                R[j] = A[q+j]
            L[n1+1] = ∞
            R[n2+1] = ∞
            i = 1
            j = 1
            for k = p to r
                if L[i] <= R[j]
                    A[k] = L[i]
                    i = i+1
                else A[k] = R[j]
                    j = j+1

* **Average Case:** O(nlogn)
* **Worst Case:** O(nlogn)

## Maximum Subarray Problem:
**Pseudocode for maximum subarray:**

            maxsubarray(A, low, high)
                if high == low
                    return (low, high, A[low])
                else mid = (low + high)/2
                    (left-low, left-high, left-sum) = maxsubarray(A, low, mid)
                    (right-low, right-high, right-sum) = maxsubarray(A, mid+1, high)
                    (cross-low, cross-high, cross-sum) = maxcrossing(A, low, mid, high)
                    if left-sum >= right-sum and left-sum >= cross-sum
                        return (left-low, left-high, left-sum)
                    else if right-sum >= left-sum and right-sum >= cross-sum
                        return (right-low, right-high, right-sum)
                    else return (cross-low, cross-high, cross-sum)
        
            maxcrossing(A, low, mid, high)
                left-sum = -∞
                sum = 0
                for i = mid downto low
                    sum = sum + A[i]
                    if sum > left-sum
                        left-sum = sum
                        max-left = i
                right-sum = -∞
                sum = 0
                for j = mid+1 to high
                    sum = sum + A[j]
                    if sum > right-sum
                        right-sum = sum
                        max-right = j
                return (max-left, max-right, left-sum + right-sum)

## Strassen's matrix multiplication:

**Formula:**
```py
matrix1 = [[a, b], [c, d]]
matrix2 = [[e, f], [g, h]]
```
p1 = a(f-h)
p2 = (a+b)h
p3 = (c+d)e
p4 = d(g-e)
p5 = (a+d)(e+h)
p6 = (b-d)(g+h)
p7 = (a-c)(e+f) 

```py
multiplied_matrix = [[p5+p4-p2+p6, p1+p2], [p3+p4, p1+p5-p3-p7]]
```
## Master Theorem:
**Recurrence Relation:**
```py
T(n) = aT(n/b) + f(n)
```
**Case 1:**
```py
a = b^k
```
**Case 2:**
```py
a < b^k
```
**Case 3:**
```py
a > b^k
```

**Importants:**

![unit2](https://media.discordapp.net/attachments/915830242692718633/1089531760116772934/image.png?width=581&height=683)

## Optimization Problems:

* Problem with an objective function and a set of constraints:
    * Maximize some profit 
    * Minimize some cost
  
**Techniques:**
* Greedy Algorithms
* Dynamic Programming
  
**Greedy Algorithms:**
* Divide the problem into subproblems
* For each step take the best choice at the current moment (local optimum)
* The hope: A locally optimal choice will lead to a globally optimal solution

#### Fractional Knapsack Problem:
**Pseudocode:**
```
fractional-knapsack(W, n, v, w)
    for i = 1 to n
        x[i] = 0
    for i = 1 to n
        if w[i] <= W
            x[i] = 1
            W = W - w[i]
        else x[i] = W/w[i]
            W = 0
    return x
```
**Knapsack with dynamic programming:**

```
if wi <= w:
    if bi + B[i-1,w-wi] > B[i-1,w]:
        B[i,w] = bi + B[i-1,w-wi]
    else:
        B[i,w] = B[i-1,w]
else:
    B[i,w] = B[i-1,w]
```
**To select item**
```
B[n,w] is the maximum value that can be put in a knapsack of capacity w
let i = n and k= w
if B[i,k] != B[i-1,k]:
    select item i
    k = k - wi
else:
    i = i-1
```
![ref](https://media.discordapp.net/attachments/915850002453114911/1089543580885979187/image.png?width=773&height=683)

*For reference*
