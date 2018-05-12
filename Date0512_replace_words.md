# 648. 单词替换
## 题目

在英语中，我们有一个叫做 词根(root)的概念，它可以跟着其他一些词组成另一个较长的单词——我们称这个词为 继承词(successor)。  
例如，词根an，跟随着单词 other(其他)，可以形成新的单词 another(另一个)。  

现在，给定一个由许多词根组成的词典和一个句子。你需要将句子中的所有继承词用词根替换掉。  
如果继承词有许多可以形成它的词根，则用最短的词根替换它。  

你需要输出替换之后的句子。  

示例 1:  

输入: dict(词典) = ["cat", "bat", "rat"]  
sentence(句子) = "the cattle was rattled by the battery"  
输出: "the cat was rat by the bat"  
注:  

输入只包含小写字母。  
1 <= 字典单词数 <=1000  
1 <=  句中词语数 <= 1000  
1 <= 词根长度 <= 100  
1 <= 句中词语长度 <= 1000  
## 思路
首先遍历一次词根，把每个词根都放进容器root里。然后再遍历一次句子，把每个单词都放进容器vocabulary里。    
然后遍历一次vocabulary，对于每个单词，都进行下列的判断：  
先进循环把所有词根过一遍，看看当前单词能不能找到词根，如果能就flag置0，把对于词根加进结果里。如果不能，就把当前单词加进去。  
## 代码实现
```ruby
class Solution {
public:
    string replaceWords(vector<string>& dict, string sentence) {
        vector<string> vocabulary;
        set<string> root;
        string result = "";
        int i = 0, j = 0;
        for(string temp : dict)
        {
            root.insert(temp);
        }
        while(i < sentence.size())
        {
            j = i;
            while(sentence[i] != ' ')
            {
                i++;
            }
            vocabulary.push_back(sentence.substr(j,i-j));//放进去每个单词
            i++;
        }
        int number = 0;
        for(string x: vocabulary)
        {
            number++;
            int flag = 1;
            for (int i = 0; i <100; i++)
            {
                if (root.find(x.substr(0,i)) != root.end())
                {
                    result += x.substr(0,i);
                    if(number<vocabulary.size()) 
                        result += ' ';
                    flag = 0;
                    break;
                }
            }
            if(flag==1)
            {
                result += x;
                if(number<vocabulary.size()) 
                    result += ' ';
            }
        }
        return result;
    }
};
```
