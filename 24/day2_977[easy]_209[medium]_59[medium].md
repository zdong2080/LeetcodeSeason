# [977. Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/description/)

time: O(n)\
space: O(n) 

### Need hint
first time of thinking is squart in place and bubble sort but this can be O(nlogn)\
hint: after square every elements, the middle one is smallest\
and the largest number on each side

### Idea
two pointers based solution\
minimize right and maximize left pointer so reach the middle one\
which is the smallest

### Java
``` java
class Solution {
    public int[] sortedSquares(int[] nums) {
        int n = nums.length;
    
        for(int i = 0; i < n; i++) {
            nums[i] *= nums[i];
        }

        int[] new_nums = new int[n];
        // System.out.println(new_nums[0]);

        int i = n - 1;
        int left = 0;
        int right = n - 1;
        while (left <= right) {
            if(nums[left] < nums[right]) {
                new_nums[i--] = nums[right--];
            }
            else {
                new_nums[i--] = nums[left++];
            }
        }


        return new_nums;
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
