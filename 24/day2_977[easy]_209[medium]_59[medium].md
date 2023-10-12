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

# [209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/description/)

time: O(n) \
space: O(1) 

### Idea
slide window based solution\
keep track total inside window\
if total >= target, remove element from left side of window, otherwise add element from right side

### Java
``` java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int n = nums.length;

        int l = 0;
        int r = 0;
        int window = 0;
        int res = Integer.MAX_VALUE;

        while(r < n) {
            int right = nums[r];
            if(window < target) {
                window += right;
                r++;
            }
            while(window >= target) {
                int diff = r - l;
                res = Math.min(res, diff);
                int left = nums[l];
                window -= left;
                l++;
            }
        }
        
        if(res == Integer.MAX_VALUE) {
            return 0;
        }
        return res;
    }
}
```


# [59. Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/description/)

time: O(n) \
space: O\(N^2\)

### Idea
slide window based solution\
keep track total inside window\
if total >= target, remove element from left side of window, otherwise add element from right side

### Java
``` java
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] res = new int[n][n];

        int left = 0;
        int right = n - 1;
        int top = 0;
        int bot = n - 1;

        int i = 1;
        while(i <= n * n) {
            // right
            int count = left;
            while(count <= right) {
                res[top][count] = i;
                count++;
                i++;
            }
            top++;

            // bot
            count = top;
            while(count <= bot) {
                res[count][right] = i;
                count++;
                i++;
            }
            right--;

            // left
            count = right;
            while(count >= left) {
                res[bot][count] = i;
                count--;
                i++;
            }
            bot--;

            // top
            count = bot;
            while(count >= top) {
                res[count][left] = i;
                count--;
                i++;
            }
            left++;
        }

        return res;
    }
}
```
