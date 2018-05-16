# 605. 种花问题
## 题目

假设你有一个很长的花坛，一部分地块种植了花，另一部分却没有。  
可是，花卉不能种植在相邻的地块上，它们会争夺水源，两者都会死去。  

给定一个花坛（表示为一个数组包含0和1，其中0表示没种植花，1表示种植了花），和一个数 n 。  
能否在不打破种植规则的情况下种入 n 朵花？能则返回True，不能则返回False。  

示例 1:  

输入: flowerbed = [1,0,0,0,1], n = 1  
输出: True  
示例 2:  

输入: flowerbed = [1,0,0,0,1], n = 2  
输出: False  
注意:  

数组内已种好的花不会违反种植规则。  
输入的数组长度范围为 [1, 20000]。  
n 是非负整数，且不会超过输入数组的大小。  
## 思路
这道题主要思路是遍历一次数组看看总共能种多少花，和要种的总数作比较。  
开头和结尾的地方有点麻烦，要单独处理比较方便。  
## 代码实现
```ruby
class Solution {
public:
    bool canPlaceFlowers(vector<int>& flowerbed, int n) {
        int i,count=0;
        if(flowerbed[0]==0 && flowerbed[1]==0)
        {
            count++;
            flowerbed[0]=1;
        }
        for(i=1;i<flowerbed.size()-1;i++)
        {
            if(flowerbed[i-1]==0 && flowerbed[i]==0 && flowerbed[i+1]==0)
            {
                count++;
                flowerbed[i]=1;
            }
        }
        if(flowerbed[i-1]==0 && flowerbed[i]==0)
        {
            count++;
        }
        if(count>=n)
            return true;
        return false;
    }
};
```
