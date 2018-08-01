# Fizz Buzz

## Description

Write a program that outputs the string representation of numbers from 1 to *n*.

But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.

## Solution

## Code

```java
public class Solution {// Not using "%" operation
    public List<String> fizzBuzz(int n) {
        List<String> ret = new ArrayList<String>(n);//向上转型
        for(int i=1,fizz=0,buzz=0;i<=n ;i++){
            fizz++;
            buzz++;
            if(fizz==3 && buzz==5){
                ret.add("FizzBuzz");
                fizz=0;//清零
                buzz=0;
            }else if(fizz==3){
                ret.add("Fizz");
                fizz=0;//清零
            }else if(buzz==5){
                ret.add("Buzz");
                buzz=0;//清零
            }else{
                ret.add(String.valueOf(i));//整型转字符串
            }
        } 
        return ret;
    }
}
```

