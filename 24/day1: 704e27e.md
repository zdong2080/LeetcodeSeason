# [704.BinarySearch](https://leetcode.com/problems/binary-search/)

time: O(logn)\
space: O(1) 

### Idea
two pointers based solution\
minimize search range inclusively in each loop

### Java
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

time: O(n) \
space: O(1) 

### Idea
two pointers based solution\
keep track element on right pointer\
if element on right is not value, add left by 1 and copy to position on left\
return left + 1

### Java
``` java
class Solution {
    public int removeElement(int[] nums, int val) {
        int left = -1;
        int right = 0;
        int n = nums.length;

        while(right < n) {
            if(nums[right] != val) {
                left++;
                nums[left] = nums[right];
            }
            right++;
        }

        return left + 1;
    }
}
```
