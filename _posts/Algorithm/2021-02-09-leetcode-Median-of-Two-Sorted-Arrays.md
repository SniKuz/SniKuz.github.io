---
title: "LeetCode - Median of Two Sorted Arrays(Hard)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/median-of-two-sorted-arrays/submissions/)
+ Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

+ Follow up: The overall run time complexity should be O(log (m+n)).
---
**Example**
```
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.

Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.substring.

Input: nums1 = [0,0], nums2 = [0,0]
Output: 0.00000

Input: nums1 = [2], nums2 = []
Output: 2.00000
```
---
+ 문제 1차 풀이
  1. 배열 2개를 합친 이후 중앙값을 찾아서 리턴
---
```
//C#
public class Solution {
    public double FindMedianSortedArrays(int[] nums1, int[] nums2) {
        int len = (nums1.Length+nums2.Length);
        int[] sorted = new int[len];
        double result = 0;
        int cnt1=0;
        int cnt2=0;
        int i = 0;
        
        while(cnt1<nums1.Length && cnt2<nums2.Length){
            if(nums1[cnt1] <= nums2[cnt2])
                sorted[i++] = nums1[cnt1++];
            else
                sorted[i++] = nums2[cnt2++];
        }
        if(cnt1>=nums1.Length){
            while(cnt2<nums2.Length){
                sorted[i++] = nums2[cnt2++];
            }
        }
        else{
            while(cnt1<nums1.Length){
            sorted[i++] = nums1[cnt1++];
            }
        }
        
        result = len%2 == 0? (sorted[len/2-1]+sorted[len/2])/2.0 : sorted[len/2];
        return result;
    }
}
```
+ Runtime: 116 ms, faster than 89.86% of C# online submissions for Median of Two Sorted Arrays.
+ Memory Usage: 28.8 MB, less than 8.61% of C# online submissions for Median of Two Sorted Arrays.Characters.


---
배운점
  1. 개인적으로는 고민을 해서 깔끔하게 작성해보려고 시도한 방식.
  2. 미리 선언한 것들이 많은 것 때문인지 메모리가 큰데 고민 필요.