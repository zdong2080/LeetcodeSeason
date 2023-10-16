# [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)

time: O(s + t)\
space: O(s + t) 

### Idea
HashMap related topic

### Java
``` java
class Solution {
    public boolean isAnagram(String s, String t) {
        Map<Character, Integer> map1 = new HashMap<>();
        Map<Character, Integer> map2 = new HashMap<>();
        char[] charArray = s.toCharArray();
        for(Character c : charArray) {
            if(map1.containsKey(c))
                map1.put(c, map1.get(c) + 1);
            else
                map1.put(c, 1);
        }

        charArray = t.toCharArray();
        for(Character c : charArray) {
            if(map2.containsKey(c))
                map2.put(c, map2.get(c) + 1);
            else
                map2.put(c, 1);
        }

        return map1.equals(map2);
    }
}
```


# [349. Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/description/)

time: O(s + t)\
space: O(s + t) 

### Idea
If set1 for nums1 is smaller, we loop through set1 and add the element to res list if \
there is an element also in set2 for nums2

### Java
``` java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> set1 = new HashSet<>();
        Set<Integer> set2 = new HashSet<>();
        List<Integer> res = new ArrayList<>();

        for(int i = 0; i < nums1.length; i++) {
            set1.add(nums1[i]);
        }
        for(int i = 0; i < nums2.length; i++) {
            set2.add(nums2[i]);
        }

        if(set1.size() < set2.size()) {
            for (Integer num : set1) {
                if(set2.contains(num))
                    res.add(num);
            }
        }
        else {
            for (Integer num : set2) {
                if(set1.contains(num))
                    res.add(num);
            }
        }

        return arrayListToIntArray(res);
    }

    public static int[] arrayListToIntArray(List<Integer> list) {
        int[] intArray = new int[list.size()];

        for (int i = 0; i < list.size(); i++) {
            intArray[i] = list.get(i);
        }

        return intArray;
    }
}
```


# [202. Happy Number](https://leetcode.com/problems/happy-number/description/)

time: O(?) \
space: O(?) 

### Idea
Basically, this algorithm maintain a hashset to store all number that is sum of all digits \
in each round. If any time a number appear twice, that means there is a loop in this n \
and n is not happy number. In contrast, if there is a sum 1, it means n is happy number.

### Java
``` java
class Solution {
    public boolean isHappy(int n) {

        Set<Integer> myset = new HashSet<>();
        int sum = 0;
        int digit = 0;
        while(true) {
            
            while(n != 0) {
                digit = n % 10;
                sum += digit * digit;
                n /= 10;
            }

            if(sum == 1)
                return true;

            if(myset.contains(sum))
                break;
            
            n = sum;
            myset.add(sum);

            sum = 0;

        }
        return false;
        
    }
}
```


# [1. Two Sum](https://leetcode.com/problems/two-sum/)

time: O(n) \
space: O(n)

### Idea
done this before

### Java
``` java
class Solution {
    public int[] twoSum(int[] nums, int target) {

        HashMap<Integer, Integer> map = new HashMap<>();

        for(int i = 0; i < nums.length; i++) {
            if(map.containsKey(target - nums[i])) {
                return new int[] {map.get(target - nums[i]), i};
            }
            map.put(nums[i], i);
        }
        
        return new int[1];
    }
}
```
