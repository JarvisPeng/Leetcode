[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)  
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.  
An input string is valid if:  
* Open brackets must be closed by the same type of brackets.
* Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.  
Example 2:Input: "()[]{}"  Output: true  
Example 3:  Input: "(]"  Output: false  
Example 4:  Input: "([)]"  Output: false  
# solution
```C++
class Solution {
public:
    bool isValid(string s) {
        int length;
        length = s.length();
        if (length == 0) {//初步筛选
            return true;
        }else if (length%2!=0){
            return false;
        }
        string::iterator i = s.begin();
        vector<char> v;//用栈保存未匹配的符号
        v.push_back(' ');//保证向量末尾有值
        v.push_back(*i);
        char chars[6] = {'(', ')', '{', '}', '[',']'};
        for (i = i+1; i != s.end(); ++i) {
                if (v.back() == chars[0]){
                    if (*i == chars[1]){
                        v.pop_back();//匹配成功
                    }else{
                        v.push_back(*i);//匹配失败
                    }
                }else if (v.back() == chars[2]){
                    if (*i == chars[3]){
                        v.pop_back();
                    }else{
                        v.push_back(*i);
                    }
                }else if (v.back() == chars[4]){
                    if (*i == chars[5]){
                        v.pop_back();
                    }else{
                        v.push_back(*i);
                    }
                }
            }
        if (v.size()==1) {//除了空，全部匹配成功
            return true;
        }else{
            return false;
        }
    }
};
```
