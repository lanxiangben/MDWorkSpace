# Reverse String

## Description

Write a function that takes a string as input and returns the string reserved.

Example：

Given s = "hello",return "olleh".

## Solution

```java
public class Solution {
    public String reverseString(String s) {
        char[] word = s.toCharArray();//转化成字符数组
        int i = 0;
        int j = s.length() - 1;
        while (i < j) {//首尾交换位置，由两端向中间
            char temp = word[i];
            word[i] = word[j];
            word[j] = temp;
            i++;
            j--;
        }
        return new String(word);//还原成字符串
    }
}
```

