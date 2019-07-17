34. 丑数 -- done
```java
public int GetUglyNumber_Solution(int index) {
    if(index <= 0) {
        return 0;
    }
    int[] uglyNumberArray = new int[index+1];
    uglyNumberArray[1] = 1;
    int twoIndex = 1;
    int threeIndex = 1;
    int fiveIndex = 1;
    int p = 2;
    while(p <= index) {
        int uglyNumber = Math.min(Math.min(2*uglyNumberArray[twoIndex], 3*uglyNumberArray[threeIndex]), 5*uglyNumberArray[fiveIndex]);
        uglyNumberArray[p++] = uglyNumber;
        if(2*uglyNumberArray[twoIndex] == uglyNumber) {
            twoIndex++;
        }
        if(3*uglyNumberArray[threeIndex] == uglyNumber) {
            threeIndex++;
        }
        if(5*uglyNumberArray[fiveIndex] == uglyNumber) {
            fiveIndex++;
        }
    }
    return uglyNumberArray[index];
}
```


3. 二维数组中的查找 -- done
```java
public boolean Find(int target, int[][] array) {
    if(array==null || array.length==0 || array[0]==null || array[0].length==0) {
        return false;
    }
    int rows = array.length;
    int cols = array[0].length;
    int row = rows-1;
    int col = 0;
    while(row>=0 && col<cols) {
        if(target == array[row][col]) {
            return true;
        } else if(target > array[row][col]) {
            col++;
        } else if(target < array[row][col]) {
            row--;
        }
    }
    return false;
}
```

9. 斐波那契数列 -- done
```
public int getFibonacci(int index) {
    if(index <= 0) {
        return 0;
    }
    if(index==1 || index==2) {
        return 1;
    }
    int low = 1;
    int high = 1;
    index -= 2;
    while(index-- > 0) {
        int tmp = low + high;
        low = high;
        high = tmp;
    }
    return high;
}
```


10. 二进制中1的个数 -- done
```java
public int getNumberOfOne(int n) {
    int count = 0;
    while(n != 0) {
        count++;
        n = n & (n-1);
    }
    return count;
}
```


11. 数值整数次方 -- done
```java
public double Power(double base, int exponent) {
    if(exponent == 0) {
        return 1;
    }
    if(exponent < 0) {
        base = 1 / base;
        exponent *= -1;
    }
    return doPower(base, exponent);
}

private double doPower(double base, int exponent) {
    if(exponent == 1) {
        return base;
    }
    double half = doPower(base, exponent / 2);
    if(exponent%2 == 0) {
        return half * half;
    } else {
        return half * half * base;
    }
}
```


5. 从尾到头打印链表 -- done
```java
public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
    ArrayList<Integer> list = new ArrayList<Integer>();
    reverseVisitList(list, listNode);
    return list;
}

private void reverseVisitList(ArrayList<Integer> list, ListNode node) {
    if(node == null) {
        return;
    }
    reverseVisitList(list, node.next);
    list.add(node.val);
}
```


16. 反转链表 -- done
```java
public ListNode reverseListOpt(ListNode head) {
    ListNode node = new ListNode(-1);
    ListNode next = null;
    while(head != null) {
        next = head.next;
        head.next = node.next;
        node.next = head;
        head = next;
    }
    return node.next;
}
```


17. 合并两个排序的列表 -- done
```java
public ListNode Merge(ListNode list1, ListNode list2) {
    ListNode head = new ListNode(-1);
    ListNode p = head;
    while(list1!=null && list2!=null) {
        if(list1.val <= list2.val) {
            p.next = list1;
            p = p.next;
            list1 = list1.next;
        } else {
            p.next = list2;
            p = p.next;
            list2 = list2.next;
        }
    }
    while(list1 != null) {
        p.next = list1;
        p = p.next;
        list1 = list1.next;
    }
    while(list2 != null) {
        p.next = list2;
        p = p.next;
        list2 = list2.next;
    }
    return head.next;
}
```

39. 二叉树的深度 -- done
```java
public int TreeDepth(TreeNode root) {
    if(root == null) {
        return 0;
    }
    int leftDepth = TreeDepth(root.left);
    int rightDepth = TreeDepth(root.right);
    return 1 + Math.max(leftDepth, rightDepth);
}

```


### utils

```java
public class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    
    public TreeNode(int val) {
        this.val = val;
    }
}

public class ListNode {
    int val;
    ListNode next;
    
    public ListNode(int val) {
        this.val = val;
    }
}
```
