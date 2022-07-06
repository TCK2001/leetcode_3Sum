# leetcode_3Sum
+ 3개의 숫자의 합이 0이 나오는 값을 구해라
+ 3個數字總合為0的值

-----
+ Example1
```
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
```
----
+ Example2
```
Input: nums = []
Output: []
```
----
+ Example3
```
Input: nums = [0]
Output: []
```
----
```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        res = []
        nums.sort() # 오름차순으로 정렬
        
        for i ,value in enumerate(nums): 
            if i > 0 and value == nums[i-1]: # 만약 현재위치가 앞에꺼랑 같으면 패스 다음거 체크
                continue
                
            l,r = i + 1, len(nums) - 1 # l은 현재위치보다 앞에 한칸꺼 r은 맨뒤에꺼
            
            while l < r: # out of range 방지
                Tsum = value + nums[l] + nums[r] # 판단
                if Tsum > 0: # 만약 3대 더한값이 0보다크면 맨뒤에서 앞으로 한칸 떙김 왜냐면 너무 큰값을 더해서 +가 나옴 그래서 큰 값인 r을 줄여줘야함
                    r -= 1
                elif Tsum < 0: # 같은원리 단 여기는 작은값이 너무 커서 < 0이 나옴 그래서 작은값을 조금 크게 만들어야해서 l + 1
                    l += 1
                else: # 더했을때 0 이 나온경우 
                    res.append([value,nums[l],nums[r]])
                    l += 1 # 다음칸으로 이동
                    while nums[l] == nums[l-1] and l < r: # 여기서 중요한거 다음칸으로 이동했을때 전에 판단했을때랑 같은 값이면 다다음칸으로 이동
                        l += 1
                    
        return res
```
---
결론 : 
중복판단이 매우 중요
```
...
if i > 0 and value == nums[i-1]: # 만약 현재위치가 앞에꺼랑 같으면 패스 다음거 체크
                continue
...
...
...
while nums[l] == nums[l-1] and l < r: # 여기서 중요한거 다음칸으로 이동했을때 전에 판단했을때랑 같은 값이면 다다음칸으로 이동
                        l += 1

참고 : NeetCode (youtube)
```
---
結論 : 
排除重複是這一題的重點
```
...
if i > 0 and value == nums[i-1]: # 만약 현재위치가 앞에꺼랑 같으면 패스 다음거 체크
                continue
...
...
...
while nums[l] == nums[l-1] and l < r: # 여기서 중요한거 다음칸으로 이동했을때 전에 판단했을때랑 같은 값이면 다다음칸으로 이동
                        l += 1

參考 : NeetCode (youtube)
```
---
### Result
Runtime: 1173 ms, faster than 59.17% of Python3 online submissions for 3Sum.\
Memory Usage: 18.1 MB, less than 41.91% of Python3 online submissions for 3Sum.
