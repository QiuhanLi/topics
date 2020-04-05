
# Binary Search

- 参考模版：
- https://segmentfault.com/a/1190000016825704
- https://github.com/labuladong/fucking-algorithm/blob/master/%E7%AE%97%E6%B3%95%E6%80%9D%E7%BB%B4%E7%B3%BB%E5%88%97/%E4%BA%8C%E5%88%86%E6%9F%A5%E6%89%BE%E8%AF%A6%E8%A7%A3.md


```java
// 标准模版
class BinarySearch {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        while (left <= right) {
            int mid = left + ((right - left) >> 1);
            if (nums[mid] == target) return mid;
            else if (nums[mid] > target) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        return -1;
    }
}

// 左边界
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return nums[left] == target ? left : -1;
    }
}

// 万能
class Solution {
	public int search(int[] nums, int target) {
		int left = 0;
		int right = nums.length - 1;
		while (left + 1 < right) {
			int mid = left + (right - left) / 2;
			if (nums[mid] < target) {
				left = mid;
			} else {
				right = mid;
			} else {
				// depend on intent when find target
			}
		}
		// post processing
		if (nums[left] == target) {
			return left;
		} else if (nums[right] == target) {
			return right;
		} else {
			return -1;
		}
	}
}
```

## 代表例题

* [374. Guess Number Higher or Lower]()
* [278. Find the first bad version]()
* [162.	Find Peak Element]()
* [34. Find First and Last Position of Element in Sorted Array]()
* [33. Search in Rotated Sorted Array]()
* [81. Search in Rotated Sorted Array II]()
* [69. sqrt(x)]()
* [153. Find Minimum in Rotated Sorted Array]()
* [154. Find Minimum in Rotated Sorted Array II]()
* [475. Heaters]()
* [74. Search a 2D Matrix]()
* [240. Search a 2D Matrix II]()
* [4. Median of Two Sorted Arrays]()
* [162. Find Peak Element]()
* [35. Search Insert Position]()
* [350. Intersection of Two Arrays II]()

## Time Complexity

O(logN)
worst case O(n) 有重复元素

## Space Complexity

O(1)
