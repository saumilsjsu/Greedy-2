# Problem 1 - Candy
## Time Complexity :
O(n)

## Space Complexity :
O(n)

## Did this code successfully run on Leetcode :
Yes.

## Any problem you faced while coding this :
No. 

## Your code here along with comments explaining your approach
### Solution:
      class Solution:
          def candy(self, ratings: List[int]) -> int:
              if not ratings or len(ratings)==0:
                  return 0
              candies=[1]*len(ratings)
              #left pass
              for i in range(1,len(ratings)):
                  if ratings[i]>ratings[i-1]:
                      candies[i]=1+candies[i-1]
              #right pass
              for i in range(len(ratings)-2,-1,-1):
                  if ratings[i]>ratings[i+1]:
                      candies[i]=max(candies[i],1+candies[i+1])

              sum=0
              for candy in candies:
                  sum+=candy
              return sum

# Problem 2 - Task Scheduler
## Time Complexity :
O(n)

## Space Complexity :
O(n)

## Did this code successfully run on Leetcode :
Yes.

## Any problem you faced while coding this :
No. 

## Your code here along with comments explaining your approach
### Solution:
      from collections import Counter
      class Solution:
          def leastInterval(self, tasks: List[str], n: int) -> int:
              if not tasks:
                  return 0

              task_count = list(Counter(tasks).values())

              max_freq = max(task_count)

              max_count = task_count.count(max_freq)

              partitions = max_freq - 1

              empty_slots = (n - (max_count - 1)) * partitions

              pending_tasks = len(tasks) - (max_freq * max_count)

              idle = max(0, empty_slots - pending_tasks)

              return len(tasks) + idle
