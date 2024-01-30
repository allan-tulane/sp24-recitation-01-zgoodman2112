# CMPS 2200  Recitation 01

**Name (Team Member 1):**Zach Goodman 
**Name (Team Member 2):**_________________________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`. All tests are in `test_main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest test_main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: your answer goes here**

The worst case input value for 'key' is the same for both 'linear_search' and 'binary_search'. This is, when the key does not exist in the list.

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`?

The best case input value for 'key' is different for 'linear_search' and 'binary_search'. Since the first element checked in 'linear_search', is the element at index 0, it'd be the best case scenario if key was at element 0. However, since the first element checked in 'binary_search' is the element in the middle of the list, it'd be most ideal if key was directly in the middle of the list.

**TODO: your answer goes here**

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest test_main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

**TODO: add your timing results here:

|        n |   linear |   binary |
|----------|----------|----------|
|       10 |    0.002 |    0.003 |
|      100 |    0.004 |    0.002 |
|     1000 |    0.041 |    0.003 |
|    10000 |    0.425 |    0.011 |
|   100000 |    5.902 |    0.033 |
|  1000000 |  107.374 |    0.035 |
| 10000000 | 1382.095 |    0.058 |**

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**TODO: your answer goes here:

Other than the first 2-3 cases for binary, yes, these theoretical running times match my empirical results. This is because with linear search, as n increases, the runtime should increase much quicker, because it is less efficient than binary search. This is proven true by the numbers, and the only inconsistency is how the first 3 values for n have approximately the same runtime for binary.**

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **TODO: your answer goes here**  O(k*n)

  + For binary search? **TODO: your answer goes here** O(n^2 + k*log_2(n))
  
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **TODO: your answer goes here**

First we need to set up the equation and simplify by isolating k.

n^2 + k*log_2(n) < kn =
n^2 < kn - k*log_2(n) = 
n^2 < k(n - log_2(n)) = 
(n^2)/(n - log_2(n)) < k = 
k > (n^2)/(n - log_2(n))

So when k is greater than (n^2)/(n - log_2(n)), it is more efficient to first sort and then use binary search rather than just using linear search without sorting. 