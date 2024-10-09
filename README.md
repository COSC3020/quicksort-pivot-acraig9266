I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
# Quicksort Pivots

In the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

# Analysis and Reasoning
The method of median of three would be slightly more likely than left-most is to select a good pivot.

When 2 or more of three chosen elements are within the middle of the array values, it is impossible to pick a pivot which is not 
within the middle 1/2 of the array values. It is still possible to pick a good pivot when only 1 of the 3 chosen elements is a good
pivot. Thus, the probability of picking a good pivot is:

P(2 elements within n/4 to 3n/4) + P(3 elements within n/4 to 3n/4) + P(1 element is in n/4 to 3n/4 and chosen as median of the three)

Using a truth table, there are 8 possible cases with each case being equally likely.

| a | b | c | Description                   |
|---|---|---|-------------------------------|
| T | T | T | Guaranteed good pivot         |
| T | T | F | Guaranteed good pivot         |
| T | F | T | Guaranteed good pivot         |
| T | F | F | Possible good pivot           |
| F | T | T | Guaranteed good pivot         |
| F | T | F | Possible good pivot           |
| F | F | T | Possible good pivot           |
| F | F | F | Guaranteed bad pivot          |

4 guaranteed good pivot cases = 4 x .125 = 0.5

3 possible good pivot cases = 3(# of cases) x .125(prob of case occuring) x 1/3(prob the good choice is the median) = 0.125

P(good pivot using median-of-three) = 0.625
