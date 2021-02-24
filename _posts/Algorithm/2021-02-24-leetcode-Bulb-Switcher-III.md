---
title: "  Bulb Switcher III(Medium)"
excerpt: ""
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/bulb-switcher-iii/)
+ There is a room with n bulbs, numbered from 1 to n, arranged in a row from left to right. Initially, all the bulbs are turned off.
+ At moment k (for k from 0 to n - 1), we turn on the light[k] bulb. A bulb change color to blue only if it is on and all the previous bulbs (to the left) are turned on too.
+ Return the number of moments in which all turned on bulbs are blue.
**Example**
```
Input: light = [2,1,3,5,4]
Output: 3
Explanation: All bulbs turned on, are blue at the moment 1, 2 and 4.
```

```
//Python
class Solution(object):
    def numTimesAllBlue(self, light):
        """
        :type light: List[int]
        :rtype: int
        """
        result = 0
        lightList = []
        append = lightList.append
        Sort = lightList.sort
        blueTime = [[j for j in range(1, i + 1)] for i in range(1, len(light) + 1)]
        for i in light:
            append(i)
            Sort()
            print(lightList)
            if lightList in blueTime:
                result += 1
        return result
//Solution 다른분거
class Solution(object):
    def numTimesAllBlue(self, light):
        """
        :type light: List[int]
        :rtype: int
        """
        rst = 0
        cur_max = 0
        for i, l in enumerate(light):
            cur_max = max(cur_max, l)
            # everytime meet max, increase rst
            if i + 1 == cur_max:
                rst += 1
        return rst
```
+ Runtime: 344 ms, faster than 79.12% of Python online submissions for Bulb Switcher III.
+ Memory Usage: 19.1 MB, less than 37.36% of Python online submissions for Bulb Switcher III.
---
처음 거에 경우 가능한 경우 전체 선언 및 계속 정렬을 하는 등 매우 비효율적...
이후 다른 분걸 참고하면서 알았는데, 문제에서 전등을 킬 수는 있지만 끄는 경우는 없다는 것을 확인...<br>Solution의 경우 이런 특성을 활용해 i번째 일때 무조건 i까지의 전등이 다 켜져 있어야 한다는 것을 활용.