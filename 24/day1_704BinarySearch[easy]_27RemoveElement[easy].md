# [704.BinarySearch](https://leetcode.com/problems/binary-search/)

平均时间复杂度O(logn) \
空间复杂度O(1) 

## Idea
index based solutions, minimize search range inclusively in each loop

``` java
class Solution {
    public int search(int[] nums, int target) {
        
        int left = 0;
        int right = nums.length - 1;
        int mid = 0;

        while(left <= right) {
            mid = left + (right - left) / 2;
            if(nums[mid] == target)
                return mid;
            else if(nums[mid] < target) {
                left = mid + 1;
            }
            else {
                right = mid - 1;
            }
        }

        return -1;
    }
}

```

# [27. Remove Element](https://leetcode.com/problems/remove-element/description/)

平均时间复杂度O(logn) \
空间复杂度O(1) 

## Idea
index based solutions, minimize search range inclusively in each loop

``` java
class Solution {
    public int search(int[] nums, int target) {
        
        int left = 0;
        int right = nums.length - 1;
        int mid = 0;

        while(left <= right) {
            mid = left + (right - left) / 2;
            if(nums[mid] == target)
                return mid;
            else if(nums[mid] < target) {
                left = mid + 1;
            }
            else {
                right = mid - 1;
            }
        }

        return -1;
    }
}

```
