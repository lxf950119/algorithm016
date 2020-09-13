# Week 1 作业合集

> **注：** 题目做了部分，有的没来得及刷，先记录，有空补上

## 一、数组

####  [删除排序数组中的重复项](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/) 

```java
public int removeDuplicates(int[] nums) {
    if(nums == null || nums.length <= 0) return 0;
    int currentIndex=0;
    for(int i=1,length=nums.length;i<length;i++) {
        if(nums[i]!=nums[currentIndex]) {
            nums[++currentIndex] = nums[i];
        }
    }
    return currentIndex+1;
}
```

####  [旋转数组](https://leetcode-cn.com/problems/rotate-array/) 

```java
public void rotate(int[] nums, int k) {
    if(nums==null||nums.length==0) return;
    k %= nums.length;
    int end=nums.length-1;
    //1、先全部翻转 -> 7,6,5,4,3,2,1
    reverseArray(nums,0,end);
    //2、翻转[0,k-1]坐标数字 ->5,6,7,4,3,2,1
    reverseArray(nums,0,k-1);
    //3、翻转[k-1,nums.length-1] ->5,6,7,1,2,3,4
    reverseArray(nums,k,end);      
}

public void reverseArray(int[] nums,int start,int end) {
    while(start < end) {
        int temp = nums[start];
        nums[start++] = nums[end];
        nums[end--] = temp; 
    }
}
```

####  [合并两个有序数组](https://leetcode-cn.com/problems/merge-sorted-array/) 

####  [两数之和](https://leetcode-cn.com/problems/two-sum/) [Day3]

####  [移动零](https://leetcode-cn.com/problems/move-zeroes/) 

```java
public void moveZeroes(int[] nums) {
    if(nums==null||nums.length<=0) return;
    int currentIndex=0;
    for(int num:nums){
        if(num != 0) nums[currentIndex++]=num;
    }
    for(int i=currentIndex;i<nums.length;i++) {
        nums[i] = 0;
    }
}
```

####　 [加一](https://leetcode-cn.com/problems/plus-one/)[Day2]

####  [接雨水](https://leetcode.com/problems/trapping-rain-water/) 

### Array实战题目

#### [11、盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/)

```java
public int maxArea(int[] height) {
    if(height==null || height.length==0) return 0;
    int i=0,j=height.length-1;
    int maxArea=0;
    while(i<j){
        int minHeight=height[i]<height[j]?height[i++]:height[j--];
        maxArea=Math.max(maxArea,(j-i+1)*minHeight);
    }
    return maxArea;
}
```

####  70、Climbing Stairs 爬楼梯[Day1]

```java
 public int climbStairs(int n) {
     if(n<=3) return n;
     int oneStep=3;
     int twoStep=2;
     int sum=0;
     for(int i=4;i<=n;i++){
         // i是当前步，当前步到达方式
         sum=oneStep+twoStep;
         // 规划下一步
         twoStep=oneStep;
         oneStep=sum;
     }
     return sum;
 }
```





## 二、链表

####  [合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/) [Day5]

### Linked List 实战题目

####   206、Reverse Linked List反转链表

```java
/**
 * 反转链表
 * 输入: 1->2->3->4->5->NULL
 * 输出: 5->4->3->2->1->NULL
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        if(head==null) return null;
        ListNode currentNode=head;
        ListNode preNode=null;
        while(currentNode!=null) {
            ListNode next=currentNode.next;
            currentNode.next=preNode;
            preNode=currentNode;
            currentNode=next;
        }
        return preNode;
    }
}
```

#### 24、两两交换链表中的节点[Day4]

####  141、 Linked List Cycle环形链表

#### 142、Linked List Cycle II 

####  25、 Reverse Nodes in k-Group k个一组翻转链表





## 三、队列、栈

####  用 add first 或 add last 这套新的 API 改写 Deque 的代码 

####  分析 Queue 和 Priority Queue 的源码 

####  [设计循环双端队列](https://leetcode.com/problems/design-circular-deque) [Day7]

#### 20、[有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)

```java
 public boolean isValid(String s) {
     if(s==null||s=="") return true;
     if(s.length()%2!=0) return false;
     Stack<Character> stack=new Stack<>();
     for(int i=0,length=s.length();i<length;i++) {
         char c=s.charAt(i);
         if(c=='{'||c=='['||c=='(') stack.push(c);
         else {
             if(stack.isEmpty()) return false;
             char preChar=stack.pop();
             if(c=='}'){
                 if(preChar!='{') return false;
             }else if(c==']'){
                 if(preChar!='[') return false;
             }else if(c==')'){
                 if(preChar!='(') return false;
             }
         }
     }
     return stack.isEmpty();
 }
```

#### [155、 最小栈](https://leetcode-cn.com/problems/min-stack/)

#### [84、 柱状图中最大的矩形](https://leetcode-cn.com/problems/largest-rectangle-in-histogram/)

#### [239、滑动窗口最大值](https://leetcode-cn.com/problems/sliding-window-maximum/)



## 每日一题

#### 

#### 猜数字游戏[Day6]















