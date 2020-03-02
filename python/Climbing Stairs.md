```python3
class Solution:
    def climbStairs(self, n: int) -> int:
        def F(m): #阶乘
            x = 1
            for i in range(m):
                x*=(i+1)
            return x
        max_m = n//2
        stairs = 0
        for i in range(max_m+1):#i表示2steps的个数，
            #例如7 ：3个1 和 2个2 排列组合阶乘，然后除去1和2各自顺序； 5!/(3!*2!)=10
            stairs += int(F(n-i)/(F(i)*F(n-2*i)))
        return stairs
```
