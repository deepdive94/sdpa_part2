## EMATM0048 - Software Development: Programming and Algorithms
### Part 2

Prepared by: Rajdeep Sarkar

Nov, 2020



This part of SDPA coursework will cover the algorithm and code for the following problem statement:

Given two lists L1 and L2 of size N and M respectively, produce an output list that is L1 sorted in
such a way that the ordering of the elements is specified by the sequence of elements in L2. For
any elements in L1 that are not present in L2, append them at the end of the output-list in sorted
order.


Initialization of Lists, L1, L2 and L3.


```python
L1 = []
L2 = []
L3 = []
```

To store frequencies of the elements in L1


```python
N = int(input("Enter number of elements for L1: "))
for i in range(0, N):
    ele_L1 = int(input())
    L1.append(ele_L1) # adding the element
```

    Enter number of elements for L1: 8
    2
    6
    7
    5
    2
    6
    8
    4
    

To store frequencies of the elements in L2


```python
M = int(input("Enter number of elements for L2: "))
for i in range(0, M):
    ele_L2 = int(input())
    L2.append(ele_L2) # adding the element

```

    Enter number of elements for L2: 4
    2
    6
    4
    5
    

To print both the lists


```python
print("Input: \nL1 = ",L1)
print("L2 = ",L2)
```

    Input: 
    L1 =  [2, 6, 7, 5, 2, 6, 8, 4]
    L2 =  [2, 6, 4, 5]
    

To store distinct elements from L1


```python
# insert the list to the set
list_set = set(L1)
# convert the set to the list
unique_list = (list(list_set))

```

 Adding the frequencies of the elements of L1 in a dictionary


```python
# Creating an empty dictionary
freq = {}

for item in L1:
        if (item in freq):
            freq[item] += 1
        else:
            freq[item] = 1

```

For all elements in L2, add the elements from L1, and get their frequency from the dictionary, and add it frequency times in L3

### Complexity O(n)


```python
no = 0
for i in range(0,M):
    if (L2[i] in unique_list):
        x =  freq.get(L2[i])
        while (x > 0):
            L3.append(L2[i])
            x = x - 1
        unique_list.remove(L2[i])
```

Add remaining elements of the unique list in an array and sort it qand then append it in the L3

### Complexity O(nlogn)

where n is the size of the unique list containing remaining elements


```python
len1 = len(unique_list)
temp = []
for i in unique_list:
    temp.append(i)

temp.sort()


for i in range(0,len1):
    x = freq.get(temp[i])
    while x > 0:
        L3.append(temp[i])
        x = x - 1

print("\nOutput Sorted List = ",L3)
```

    
    Output Sorted List =  [2, 2, 6, 6, 4, 5, 7, 8]
    

1. The complexity of the sorting algorithm is  O(n)

2. The complexity of the sorting algorithm if L2 is larger than L1 will be the same as the loop will only traverse as many number of times as the number of elements in the L2.
   Even if L1 and L2 are of same size, the complexity will remain the same.





```python

```


```python

```
