# 744. 寻找比目标字母大的最小字母
## 题目
给定一个只包含小写字母的有序数组letters 和一个目标字母 target，寻找有序数组里面比目标字母大的最小字母。  

数组里字母的顺序是循环的。举个例子，如果目标字母target = 'z' 并且有序数组为 letters = ['a', 'b']，则答案返回 'a'。  

示例:  

输入:  
letters = ["c", "f", "j"]  
target = "a"  
输出: "c"  

输入:  
letters = ["c", "f", "j"]  
target = "c"  
输出: "f"  

输入:  
letters = ["c", "f", "j"]  
target = "d"  
输出: "f"  

输入:  
letters = ["c", "f", "j"]  
target = "g"  
输出: "j"  

输入:  
letters = ["c", "f", "j"]  
target = "j"  
输出: "c"  

输入:  
letters = ["c", "f", "j"]  
target = "k"  
输出: "c"  
注:  

letters长度范围在[2, 10000]区间内。  
letters 仅由小写字母组成，最少包含两个不同的字母。  
目标字母target 是一个小写字母。  
## 思路
建立一个新的容器用来放字母。然后把字母从小到大排序，如果最大的字母都比target要小，就直接返回第一个字母。
如果不是，就用while遍历看看哪个字母能刚刚好比最大的字母要小，然后返回它。
## 代码实现
```ruby
class Solution {
public:
    char nextGreatestLetter(vector<char>& letters, char target) {
        vector<char> temp(letters);
        sort(temp.begin(), temp.end());
        int size = temp.size();
        if(target >= temp[size - 1])
            return temp[0];
        int i = 0;
        while(temp[i] <= target)
        {
            i++;
        }
        return temp[i];
    }
};
```
