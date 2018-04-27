# 14. 最长公共前缀
## 题目
编写一个函数来查找字符串数组中的最长公共前缀。  

如果不存在公共前缀，返回空字符串 ""。  

##### 示例 1:  

输入: ["flower","flow","flight"]  
输出: "fl"  
##### 示例 2:  

输入: ["dog","racecar","car"]  
输出: ""  
解释: 输入不存在公共前缀。  
##### 说明:  

所有输入只包含小写字母 a-z 。  
## 思路
这道题主要就是遍历一次每个字母，比如说先把第一个字母遍历一次，检查strs里面有没有不对劲的。  
如果有不能作为公共前缀的情况，就直接返回result。  
没注意到的反而是第一个for循环里面i循环的条件。  
一开始写的时候思路还不怎么清晰，就用了i<strs.size()，然后通过了116个样例，两个没过。  
找了蛮久，发现是循环是先找每一个字母，所以要刚刚好遍历字符串的长度-1，避免提早结束循环。  
以后写东西，要先有个大概思路了才能下手，不然后期查问题有点麻烦。  
## 代码实现
```ruby
class Solution {
public:
string longestCommonPrefix(vector<string>& strs) {
if(strs.size()==0)  
return ""; 
string result;
string temp=strs[0];
for(int i=0;i < strs[0].length()-1;i++){
if(strs[i].size()==0)
return "";
for(int j=0;j<strs.size()+1;j++){
if(j==strs.size())
{
result.push_back(temp[i]);
break;
}
if(temp[i]==strs[j][i])
continue;
else 
return result;
}
}
return result;
}
};
```
