# 题目

请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy。 

# 思路

 从前向后记录‘ ’数目，从后向前替换‘ ’。 重点：从后向前替换的时候的技巧 例如：“we are lucky” 

```
0 1 2 3 4 5 6 7 8 9 10 11
w e a r e l u c k y
```

可以得知count=2;//空格的个数。   所以在替换的时候7~11的字母要向后移动count×2个位置，3~5字母要向后移动（count-1）×2个位置。 所以得到 ：

```
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
w e   a r e   l u c  k y 
w e   a r a r e u c  k l   u c   k y
```

在替换的时候直接在空格处写入%20了

```
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
w e   a r e   l u c  k y 
w e % 2 0 a r e % 2  0 l  u  c  k  y
```

# 代码

```java
public class Solution {
    public String replaceSpace(StringBuffer str) {
        int spacenum = 0;//spacenum为计算空格数
        for(int i=0;i<str.length();i++){
            if(str.charAt(i)==' ')
                spacenum++;
        }
        int indexold = str.length()-1; //indexold为为替换前的str下标
        int newlength = str.length() + spacenum*2;//计算空格转换成%20之后的str长度
        int indexnew = newlength-1;//indexold为为把空格替换为%20后的str下标
        str.setLength(newlength);//使str的长度扩大到转换成%20之后的长度,防止下标越界
        for(;indexold>=0 && indexold<newlength;--indexold){ 
                if(str.charAt(indexold) == ' '){  //
                str.setCharAt(indexnew--, '0');
                str.setCharAt(indexnew--, '2');
                str.setCharAt(indexnew--, '%');
                }else{
                    str.setCharAt(indexnew--, str.charAt(indexold));
                }
        }
        return str.toString();
    }
}
```



