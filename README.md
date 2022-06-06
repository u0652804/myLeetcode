# myLeetcode

## 45. Jump Game II

    class Solution(object):
      def jump(self, nums):
          """
          :type nums: List[int]
          :rtype: int
          549
          """
          if len(nums) > 2:
              if nums[0] > len(nums) - 1: 
                  return 1

          rst = 0    
          pre, cur = 0, 0
          for i in range(0, len(nums)):
              if i > pre:
                  rst += 1
                  pre = cur
                  # if pre > len(nums): return rst

              cur = max(cur, nums[i]+i)

          return rst
                

## 253. Meeting Rooms II

Given an array of meeting time intervals consisting of start and end times [[s1,e1],[s2,e2],...] (si < ei), find the minimum number of conference rooms required.

Example 1:

Input: 
        [[0, 30],[5, 10],[15, 20]]
        Output: 2
        
Example 2:

        Input: [[7,10],[2,4]]
        Output: 1
