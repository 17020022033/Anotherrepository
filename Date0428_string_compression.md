# 443. 压缩字符串
## 题目

给定一组字符，使用原地算法将其压缩。  

压缩后的长度必须始终小于或等于原数组长度。  

数组的每个元素应该是长度为1 的字符（不是 int 整数类型）。  

在完成原地修改输入数组后，返回数组的新长度。  

进阶：  
你能否仅使用O(1) 空间解决问题？  

示例 1：  

输入：  
["a","a","b","b","c","c","c"]  

输出：    
返回6，输入数组的前6个字符应该是：["a","2","b","2","c","3"]  

说明：  
"aa"被"a2"替代。"bb"被"b2"替代。"ccc"被"c3"替代。  
示例 2：  

输入：  
["a"]  

输出：  
返回1，输入数组的前1个字符应该是：["a"]  

说明：  
没有任何字符串被替代。  
示例 3：  

输入：  
["a","b","b","b","b","b","b","b","b","b","b","b","b"]  

输出：  
返回4，输入数组的前4个字符应该是：["a","b","1","2"]。  

说明：  
由于字符"a"不重复，所以不会被压缩。"bbbbbbbbbbbb"被“b12”替代。  
注意每个数字在数组中都有它自己的位置。  
注意：  

所有字符都有一个ASCII值在[35, 126]区间内。  
1 <= len(chars) <= 1000。  
## 思路
就用一个for循环遍历每个元素。  
主要是算出重复字母的数量之后用to_string这个函数把它转换成string类型。  
然后用一个for循环把它放进原本的字符串里面。  
今天突然发现自己没有太搞清楚chars[i++]这种类型和chars[i+1]的区别…  
如果是i++会改变i的值，i+1却不会。  
这么来看差别还蛮大的，怎么我今天才突然注意到这件事，震惊的。  
## 代码实现
```ruby
class Solution {
public:
    int compress(vector<char>& chars) {
        int start=0;
        int end=0;
        int temp=0;
        int charssize=chars.size();
        for(int end=0;end<charssize;)
        {
            if(end==charssize-1||chars[end]!=chars[end+1])
                chars[start++] = chars[end++]; 
            else{
                temp=end;
                chars[start]=chars[end];
                start++;
                while(chars[end]==chars[temp]&&end<charssize)
                    end++;
                string num=to_string(end-temp);
                    for(int i=0;i<num.size();)
                    {
                        chars[start]=num[i++];
                        start++;
                    }
            }
        }
        return start;
    }
};
```
