---
title: "LeetCode - Reverse Integer(easy)"
excerpt: "Reverse Integer"
categories: [Algorithm]
tag: [Algorithm]
---
[문제링크(클릭하세요)](https://leetcode.com/problems/reverse-integer/solution/)
+ Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

+ Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

+ Constraints:
-2^31 <= x <= 2^31 - 1


---
**Example**
```
Input: x = 123
Output: 321

Input: x = -123
Output: -321

Input: x = 120
Output: 21
```
---
+ 문제 1차 풀이
  1. 비트 연산으로 푸는 것 같지만 C#에서 해본적이 없기 때문에... 단순 조절로 문제 진행 -> wrong answer
  2. 역으로 했을 때 int 범위를 넘어가는 문제 발생. -> int를 long으로 변환 후 int 범위 넘으면 0으로 초기화 -> Clear
  3. 문제 해결 이후 비트로 푼 방법 참고
```
//C#
public class Solution {
    public int Reverse(int x) {
        long result = 0;
				long digitLv = 0;
				int temp = x;
				long longX = (long)x;
				

				while(temp != 0){
					temp /= 10;
					digitLv++;
        }
        
				while(digitLv > 0){
					result += longX%10 * pow(10, digitLv-1);
					longX = longX / 10;
					digitLv--;
				}
				if(result > pow(2, 31)-1 || pow(-2, 31) > result ) result = 0;
				return (int)result;
		}
    
    public long pow(int x, long n){
			long val = 1;
			for(int i = 1; i<=n; i++){
				val = x*val;
			}
			return val;
		}
}
```
//C++ Solution 비트 연산자
class Solution {
public:
    int reverse(int x) {
        int rev = 0;
        while (x != 0) {
            int pop = x % 10;
            x /= 10;
            if (rev > INT_MAX/10 || (rev == INT_MAX / 10 && pop > 7)) return 0;
            if (rev < INT_MIN/10 || (rev == INT_MIN / 10 && pop < -8)) return 0;
            rev = rev * 10 + pop;
        }
        return rev;
    }
};
```
+ Runtime: 44 ms, faster than 61.07% of C# online submissions for Reverse Integer.
+ Memory Usage: 15.3 MB, less than 81.74% of C# online submissions for Reverse Integer.

---
배운점
  1. 비트 연산자... 1학년 때 C 이후에는 본적이 별로 없어서 갑작스러웠다.
  2. Int 크기 초과 시 0으로 초기화에 대한 생각? 제한을 잘 생각하자.
  3. 좀 더 효율적이게? 읽기 쉬운 코드 고민해보기...
