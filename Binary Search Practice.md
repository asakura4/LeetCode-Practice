# LeetCode-Practice

## Critical Point
a. start + 1 < end 

b. start + (end - start)/2

c. discuss in 3 case: ==, <, >

d. after break condition nums[start], nums[end] compare with target


1.Classical Binary Search

Find any position of a target number in a sorted array. Return -1 if target does not exist.



    class Solution:
        """
        @param nums: An integer array sorted in ascending order
        @param target: An integer
        @return: An integer
        """
        def findPosition(self, nums, target):
            if not nums or len(nums) == 0:
                return -1

            start = 0
            end  = len(nums) -1
            while start + 1 < end:
                mid = start + (end - start)//2
                if nums[mid] == target:
                    end = mid
                elif nums[mid] < target:
                    start = mid
                else:
                    end = mid

            if nums[start] == target:
                return start

            if nums[end] == target:
                return end
            return -1
            
            

2.First Position of Target

For a given sorted array (ascending order) and a target number, 
find the first index of this number in O(log n) time complexity.

If the target number does not exist in the array, return -1.

Example 1:
Input:  [1,4,4,5,7,7,8,9,9,10]，1
Output: 0
	
Example 2:
Input: [1, 2, 3, 3, 4, 5, 10]，3
Output: 2
	
Example 3:
Input: [1, 2, 3, 3, 4, 5, 10]，6
Output: -1
	

      class Solution:
          """
          @param nums: The integer array.
          @param target: Target to find.
          @return: The first position of target. Position starts from 0.
          """
          def binarySearch(self, nums, target):
              # write your code here
              if not nums or len(nums) == 0:
                  return -1


              start = 0
              end = len(nums) -1
              while start + 1 < end:
                  mid = start + (end - start)//2
                  if nums[mid] == target:
                      end = mid
                  elif nums[mid] < target:
                      start = mid
                  else:
                      end = mid

              if nums[start] == target:
                  return start
              if nums[end] == target:
                  return end

              return -1
              
              
              
3. Last Position of Target
Find the last position of a target number in a sorted array. 
Return -1 if target does not exist.

Example 1:
Input: nums = [1,2,2,4,5,5], target = 2
Output: 2

Example 2:
Input: nums = [1,2,2,4,5,5], target = 6
Output: -1

        class Solution:
            """
            @param nums: An integer array sorted in ascending order
            @param target: An integer
            @return: An integer
            """
            def lastPosition(self, nums, target):
                # write your code here
                # write your code here
                if not nums or len(nums) == 0:
                    return -1


                start = 0
                end = len(nums) -1
                while start + 1 < end:
                    mid = start + (end - start)//2
                    if nums[mid] == target:
                        start = mid
                    elif nums[mid] < target:
                        start = mid
                    else:
                        end = mid

                if nums[end] == target:
                    return end                

                if nums[start] == target:
                    return start


                return -1
		
		
		
Search in Rotated Sorted Array

Suppose a sorted array is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.

Example
Example 1:

Input: [4, 5, 1, 2, 3] and target=1, 
Output: 2.
Example 2:

Input: [4, 5, 1, 2, 3] and target=0, 
Output: -1.		
		
	class Solution:
	    """
	    @param A: an integer rotated sorted array
	    @param target: an integer to be searched
	    @return: an integer
	    """
	    def search(self, A, target):
		# write your code here
		if not A:
		    return -1

		start = 0
		end = len(A) - 1

		while start + 1 < end:
		    mid = start + (end - start)//2
		    if target == A[mid]:
			return mid

		    if A[start] <= A[mid]:  			 # left hand side is sorted array
			if A[start] <= target <= A[mid]:	 # target in sorted array
			    end = mid
			else:					 # target in rotated sorted array
			    start = mid
		    else:		    			 # right hand side is sorted array
			if A[mid] <= target <= A[end]:		 # target in sorted array
			    start = mid
			else:					 # target in rotated sorted array
			    end = mid

		if A[start] == target:
		    return start
		if A[end] == target:
		    return end
		return -1




