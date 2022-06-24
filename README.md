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

        Input: [[0, 30],[5, 10],[15, 20]]
        Output: 2
        
Example 2:

        Input: [[7,10],[2,4]]
        Output: 1

Code :

        class Solution(object):
            def meetingRoom2(self, intervals):
                """
                  :type intervals: List[List[int]]
                  :rtype: int
                """
                
                if len(intervals) <= 1: return len(intervals)

                # s_tc : set time change 
                s_tc = set()
                for e in intervals:
                    s_tc.add(e[0])
                    s_tc.add(e[1])
                #print(s_tc)  

                rst = 1
                for v in s_tc:
                    cnt = 0
                    for e in intervals:
                        if v <= e[1] and v >= e[0]: 
                            cnt += 1
                    rst = max(rst, cnt) 
                return rst

        # test case
        m = Solution()
        print(0, m.meetingRoom2(([])))
        print(1, m.meetingRoom2([[7,10]]))
        print(2, m.meetingRoom2([[0,30],[5,10],[15,20]]))
        print(2, m.meetingRoom2([[0,30],[5,10],[15,20]]))
        print(1, m.meetingRoom2([[7,10],[2,4]]))
        print(2, m.meetingRoom2([[7,10],[2,8]]))
        print(7, m.meetingRoom2([[7,10],[2,8],[3,8],[4,8],[5,8],[6,8],[2,8]]))    
        
        # sol2 
        class Solution(object):
            def meetingRoom2(self, intervals):
                if len(intervals) <= 1: return len(intervals)

                rst = 1
                for it in intervals:
                    for v in it:
                        cnt = 0
                        for e in intervals:
                            if v <= e[1] and v >= e[0]: 
                                cnt += 1
                        rst = max(rst, cnt) 
                return rst   
