---
title: "Relative Sort Array(Easy)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/relative-sort-array/)
+ Given two arrays arr1 and arr2, the elements of arr2 are distinct, and all elements in arr2 are also in arr1.
+ Sort the elements of arr1 such that the relative ordering of items in arr1 are the same as in arr2.  Elements that don't appear in arr2 should be placed at the end of arr1 in ascending order.
---
**Example**

```
Input: arr1 = [2,3,1,3,2,4,6,7,9,2,19], arr2 = [2,1,4,3,9,6]
Output: [2,2,2,1,4,3,3,9,6,7,19]
```

+ 문제 1차 풀이
  1. 딕셔너리에 다 넣은 후 array 앞에서부터 다시 채우기
  2. arr2에 들어있지 않은 수는 sort 해줘서 뒤에 다시 넣기
```
//C#
public class Solution {
    public int[] RelativeSortArray(int[] arr1, int[] arr2) {
        Dictionary<int, int> dic = new Dictionary<int, int>();
        int resultLv = 0;
        for(int i = 0; i < arr1.Length; i++){
                if(dic.ContainsKey(arr1[i])) dic[arr1[i]] += 1;
                else dic.Add(arr1[i], 1);
        }
        foreach(var item in arr2){
            for(int i = 0; i < dic[item]; dic[item]--){
                arr1[resultLv++] = item;
            }
        }
        var queryAsc = dic.OrderBy(x => x.Key); // dictionary sort Key ascending order
        foreach(var item in queryAsc){
            if(item.Value>0){
                for(int i = 0; i < item.Value; i++){
                    arr1[resultLv++] = item.Key;
                }
            }
        }
        return arr1;
    }
}
```
+ Runtime: 240 ms, faster than 72.73% of C# online submissions for Relative Sort Array.
+ Memory Usage: 30.9 MB, less than 57.79% of C# online submissions for Relative Sort Array.
