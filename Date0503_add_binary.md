# 67. 二进制求和
## 题目
给定两个二进制字符串，返回他们的和（用二进制表示）。  

输入为非空字符串且只包含数字 1 和 0。  

示例 1:  

输入: a = "11", b = "1"    
输出: "100"    
示例 2:   

输入: a = "1010", b = "1011"  
输出: "10101"  
## 思路
这道题主要是在加的时候可能比较麻烦一点。  
就每个位比一下，如果要进位，就表示进位的next+1  
最后判断一下是不是所有要进的位都进完了。假如不是，就在结果最前面加一。  
## 代码
```ruby
class Solution {
public:
    string addBinary(string a, string b) {
        int sizea = a.size();
        int sizeb = b.size();
        if (sizea == 0)
            return b;
        if (sizeb == 0)
            return a;
        string result=a;
        int count=0;
        int next=0;
        if(sizea>sizeb)
        {
            result=a;
            count=sizea-1;
        }
        else
        {
            result=b;
            count=sizeb-1;
        }
        int temp=0;
        for (int i = sizea-1, j = sizeb-1; i >=0 || j >=0; --i, --j)
        {
            if(i>=0&&j>=0)
            {
                temp = (a[i] - '0') + (b[j] - '0') + next;
            }
            else if(i>=0)
            {
                temp = (a[i] - '0') + next;
            }
            else if(j>=0)
            {
                temp = (b[j] - '0') + next;
            }
            if (temp >= 2)
            {
                temp -= 2;
                next = 1;
            }
            else
            {
                next= 0;
            }
            result[count] = temp + '0';
            count--;
        }
        if(next==1)
            result="1"+result;
        return result;
    }
};

```
