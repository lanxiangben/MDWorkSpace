# 题目

输入一个链表，按照链表值从尾到头的顺序返回一个ArrayList。

# 思路

递归思想，本质是利用堆栈“后进先出”的特点。

# 代码

```java
public class Solution {
    ArrayList<Integer> arrayList=new ArrayList<Integer>();
    public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
        if(listNode!=null){
            this.printListFromTailToHead(listNode.next);
            arrayList.add(listNode.val);
        }
        return arrayList;
    }
}  
```

