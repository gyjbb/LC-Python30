# LC-Python30
Greedy Algorithm 5


## 435.Non-overlapping Intervals, 763.Partition Labels, 56.Merge Intervals
July 04, 2023  4h

Congratulations!\
This is the 30th day for leetcode python study. Today we will learn about the Greedy Algorithm!\
The challenges today are especially about ~~inserting items according to the ranking and merge intervals of overlapping~~.


## 435.Non-overlapping Intervals
Firstly sort all intervals according to the left boundaries. If interval i overlaps with interval i+1, update the right boundary of interval i with the max of i and i-1's right boundaries. In this way, we can compare if the i+1 interval overlaps with the former two intervals.
```python 
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        if not intervals:
            return 0
        
        intervals.sort(key = lambda x: x[0])    #sort according to left boundaries
        count = 0      #to record the number of overlapping intervals
        for i in range(1, len(intervals)):
            if intervals[i][0] < intervals[i-1][1]:     #there is overlap between i and i-1 interval
                count += 1
                #update the right boundary of i-1 and i with the min one 
                #to see if i+1 will overlap with these two
                intervals[i][1] = min(intervals[i-1][1], intervals[i][1])

        return count
```


## 763.Partition Labels
The letter in a interval can only appear in this interval.\
We define a hash table to record the furthest place one letter lies.
```python
class Solution:
    def partitionLabels(self, s: str) -> List[int]:
        last_occurrence = {}    #store the last place i each character lies
        for i, ch in enumerate(s):
            last_occurrence[ch] = i
        
        result = []
        start, end = 0, 0
        for i, ch in  enumerate(s):
            end = max(end, last_occurrence[ch])     #keep updating the end of current interval when we loop over
            if i == end:        #loop until a place where an interval meets requirement
                result.append(end-start+1)
                start = i+1     #update the start for the next interval

        return result
```


## 56.Merge Intervals
hard. 

