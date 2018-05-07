# 537. 复数乘法
## 题目
给定两个表示复数的字符串。  

返回表示它们乘积的字符串。注意，根据定义 i2 = -1 。  

示例 1:  

输入: "1+1i", "1+1i"  
输出: "0+2i"  
解释: (1 + i) * (1 + i) = 1 + i2 + 2 * i = 2i ，你需要将它转换为 0+2i 的形式。  
示例 2:  

输入: "1+-1i", "1+-1i"  
输出: "0+-2i"  
解释: (1 - i) * (1 - i) = 1 + i2 - 2 * i = -2i ，你需要将它转换为 0+-2i 的形式。   
注意:  

输入字符串不包含额外的空格。  
输入字符串将以 a+bi 的形式给出，其中整数 a 和 b 的范围均在 [-100, 100] 之间。输出也应当符合这种形式。  
## 思路
可以先找出加号的位置，通过auto这种变量就可以很方便的找到。  
然后用stoi函数把复数里的实部转换成整型后相乘。  
虚部也用类似的方法可以乘起来，最后返回结果。  
## 代码实现
```ruby
class Solution {
public:
    string complexNumberMultiply(string a, string b) {
        int n1 = a.size(), n2 = b.size();
        auto i = a.find_last_of("+");
        auto j = b.find_last_of("+");
        int a1 = stoi(a.substr(0, i));
        int b1 = stoi(b.substr(0, j));
        int a2 = stoi(a.substr(i + 1, n1 - i - 2));
        int b2 = stoi(b.substr(j + 1, n2 - j - 2));
        int result1 = a1 * b1 - a2 * b2;
        int result2 = a1 * b2 + a2 * b1;
        string result="";
        result=to_string(result1) + "+" + to_string(result2) + "i";
        return result;
    }
};
```
