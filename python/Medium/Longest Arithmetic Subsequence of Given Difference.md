[Longest Arithmetic Subsequence of Given Difference](https://leetcode.com/problems/longest-arithmetic-subsequence-of-given-difference/)  
Given an integer array __arr__ and an integer __difference__, return the length of the longest subsequence in __arr__ which is an arithmetic sequence such that the difference between adjacent elements in the subsequence equals __difference__.  
Example 3:

Input: arr = [1,5,7,8,5,3,4,2,1], difference = -2
Output: 4
Explanation: The longest arithmetic subsequence is [7,5,3,1].

Constraints:

1 <= arr.length <= 10^5
-10^4 <= arr[i], difference <= 10^4
# solution
```python3
class Solution:
    def longestSubsequence(self,arr, difference):
        res = dict()
        for num in arr:# 别人的代码
            res[num] = res.get(num-difference, 0) + 1#反过来算，记录之前每个数的个数
        return max(res.values())
#         arr_set = sorted(list(set(arr))) #difference>0升序，从最小的数开始找长度
#         if difference<0:arr_set.reverse() #difference<0升序，从最大的数开始找长度
#         # print(len(arr),arr_set)
#         max_length = 1
#         for num in arr_set:
#             if difference !=0 :
#                 if max_length>=(arr_set[-1]-arr_set[0])//difference+1:break #达到可能的最大程度 1+（最大值-最小值）/差值
#             if num not in arr: continue #该项已被删除
#             if max_length>=len(arr[arr.index(num):]):continue #已得最大长度大于剩余可行列表长度
#             if not num+(max_length)*difference in arr[arr.index(num)+1:]:#超过已得最大长度 的可行值未在后序列表中
#                 del arr[arr.index(num)]
#                 continue
#             index_f,num_length=arr.index(num),0
#             while num in arr[index_f:]:
#                 # if max_length>=len(arr[index_f:]):break #已得最大长度大于剩余可行列表长度
#                 index_f = arr[index_f:].index(num)+index_f #特定num后面序列的index
#                 del arr[index_f] #删除已经计算的值
#                 num_length+=1
#                 num+=difference
#             # num_length = get_length(arr,arr.index(num),num,0)
#             if num_length>max_length:max_length=num_length
#             # print(num,num_length,max_length)
#             # if num_length == 5:print(num,num_length,arr)
#         return max_length
```
