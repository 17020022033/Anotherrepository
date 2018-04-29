# 11. 盛最多水的容器
## 题目
给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。  
画 n 条垂直线，使得垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。  
找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。  

注意：你不能倾斜容器，n 至少是2。  
## 思路
这道题挺典型的双指针的，实现也不太难。  
分别从左边和右边开始遍历，左右指针相遇就算是遍历结束了。  
每次都判断一下是当前容器大还是历史最大值大，选大的作为result。  
遍历的时候比较一下左边和右边哪边高，就移动矮的那边，再进行遍历算新容器大小。  
## 代码实现
```ruby
class Solution {
public:
    int maxArea(vector<int>& height) {
        int left = 0;
        int right = height.size() - 1;
        int result = 0;
        while(left!=right){
            result=max(result,min(height[right],height[left])*(right-left));
            if(height[left] >= height[right])
                 right--;
            else
                 left++;
        }
        return result;
    }
};
```
