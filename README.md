# LC-Python30
Greedy Algorithm 5


## 435.Non-overlapping Intervals, 763.Partition Labels 
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




## 56. 
合并区间  hard

