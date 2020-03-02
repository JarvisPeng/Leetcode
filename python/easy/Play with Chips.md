[Play with Chips](https://leetcode.com/problems/play-with-chips/)  
There are some chips, and the i-th chip is at position chips[i].  
You can perform any of the two following types of moves any number of times (possibly zero) on any chip:   
* Move the i-th chip by 2 units to the left or to the right with a cost of 0.
* Move the i-th chip by 1 unit to the left or to the right with a cost of 1.  

There can be two or more chips at the same position initially.  
Return the minimum cost needed to move all the chips to the same position (any position).  
Example 2: Input: chips = [2,2,2,3,3]  Output: 2  
Explanation: Both fourth and fifth chip will be moved to position two with cost 1. Total minimum cost will be 2.
Constraints: 1 <= chips.length <= 100  1 <= chips[i] <= 10^9
# solution 
```python3
class Solution:
    def minCostToMoveChips(self, chips: List[int]) -> int:
        odd =dict() #奇数odd[chip]+=1个数字典
        even = dict() #偶数even[chip]=+1个数字典
        odd_sum , even_sum =0,0 #最小总个数即为答案
        for chip in chips:
            if chip%2==0:
                even_sum+=1
                if chip in even:
                    even[chip]+=1
                else:even[chip]=1
            if chip%2==1:
                odd_sum+=1
                if chip in even:
                    odd[chip]+=1
                else:odd[chip]=1
        return min([even_sum,odd_sum])
        # 其他人的一行代码，但时间复杂都高一点
        # return min(sum((c1 - c2) % 2 for c2 in chips) for c1 in chips)
```
