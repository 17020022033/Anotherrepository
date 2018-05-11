# 458. 可怜的小猪
## 题目

有1000只水桶，其中有且只有一桶装的含有毒药，其余装的都是水。它们从外观看起来都一样。如果小猪喝了毒药，它会在15分钟内死去。  

问题来了，如果需要你在一小时内，弄清楚哪只水桶含有毒药，你最少需要多少只猪？  

回答这个问题，并为下列的进阶问题编写一个通用算法。  

进阶:  

假设有 n 只水桶，猪饮水中毒后会在 m 分钟内死亡，你需要多少猪（x）就能在 p 分钟内找出“有毒”水桶？n只水桶里有且仅有一只有毒的桶。  
## 思路
这道题好可爱又好有趣耶。  
temp是检查时间除以猪会死的时间+1，这个数是一只猪可以检查的水桶数。  
如果有两只猪的话，就可以检查temp^2这么多个桶，n只猪可以检查temp^n个桶。  
这样的话就进行循环，看看什么时候可以检查的数量比桶的数量大，就返回现在所用的猪的数量就可以了。  

## 代码实现
```ruby
class Solution {
public:
    int poorPigs(int buckets, int minutesToDie, int minutesToTest) {  
    if(buckets==1) return 0;  
    int temp=minutesToTest/minutesToDie+1;  
    int dimension=1;  
    int result=0;  
    while(dimension<buckets)  
    {  
        result++;  
        dimension*=temp;  
    }  
    return result;  
}  
};
```
