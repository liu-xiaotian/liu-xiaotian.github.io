---
title: "NeetCode Roadmap"
date: 2026-03-29T12:00:00+08:00
draft: false
tags: ["Learning"]
---

- **第一阶段：核心基础**
  - Arrays & Hashing (数组与哈希表)
    - Two Pointers (双指针)
    - Stack (栈)

- **第二阶段：线性结构进阶**
  - Binary Search (二分查找)
  - Sliding Window (滑动窗口)
  - Linked List (链表)

- **第三阶段：树与堆 (核心枢纽)**
  - **Trees (树)**
    - Tries (前缀树)
    - Heap / Priority Queue (堆/优先队列)
    - Backtracking (回溯)

- **第四阶段：高级算法与图论**
  - **从堆延伸：**
    - Intervals (区间)
    - Greedy (贪心)
    - Advanced Graphs (高级图论)

  - **从回溯延伸：**
    - Graphs (图)
    - 1-D DP (一维动态规划)

- **第五阶段：深度优化与综合**
  - 2-D DP (二维动态规划)
  - Bit Manipulation (位运算)
  - Math & Geometry (数学与几何)

### 合并两个有序链表

```js
function mergeTwoLists(list1, list2) {
  // 递归终止：其中一个链表为空，直接返回另一个
  if (!list1) return list2; // list1 空了，list2 剩下的全接上
  if (!list2) return list1; // list2 空了，list1 剩下的全接上

  // 比较头节点，小的作为当前节点
  if (list1.val <= list2.val) {
    // list1 小，list1 当头
    list1.next = mergeTwoLists(list1.next, list2); // list1.next 指向合并后的结果
    return list1; // 返回当前头节点
  } else {
    // list2 小，list2 当头
    list2.next = mergeTwoLists(list1, list2.next); // list2.next 指向合并后的结果
    return list2; // 返回当前头节点
  }
}
```

执行流程：

```plain
merge(1→3→5, 2→4→6)

递去阶段（压栈）：
  1 <= 2? 是 → 1.next = merge(3→5, 2→4→6)    【暂停，等结果】
    2 <= 3? 是 → 2.next = merge(3→5, 4→6)    【暂停】
      3 <= 4? 是 → 3.next = merge(5, 4→6)     【暂停】
        4 <= 5? 是 → 4.next = merge(5, 6)      【暂停】
          5 <= 6? 是 → 5.next = merge(null, 6)【暂停】
            list1 为空 → return list2(6)      【返回 6】

回溯阶段（弹栈，执行 return）：
  5.next = 6 → return 5        【返回 5→6】
  4.next = 5→6 → return 4      【返回 4→5→6】
  3.next = 4→5→6 → return 3    【返回 3→4→5→6】
  2.next = 3→4→5→6 → return 2  【返回 2→3→4→5→6】
  1.next = 2→3→4→5→6 → return 1【返回 1→2→3→4→5→6】
```

r=0 'a': 窗口[a] l=0, 长度=1, max=1
r=1 'b': 窗口[ab] l=0, 长度=2, max=2  
r=2 'c': 窗口[abc] l=0, 长度=3, max=3 ← 目前最长
r=3 'a': 'a'重复(在0) l=max(0+1,0)=1, 窗口[bca], 长度=3, max=3
r=4 'b': 'b'重复(在1) l=max(1+1,1)=2, 窗口[cab], 长度=3, max=3
r=5 'c': 'c'重复(在2) l=max(2+1,2)=3, 窗口[abc], 长度=3, max=3
r=6 'b': 'b'重复(在4) l=max(4+1,3)=5, 窗口[cb], 长度=2, max=3
r=7 'b': 'b'重复(在6) l=max(6+1,5)=7, 窗口[b], 长度=1, max=3

结果: 3 ("abc")

lengthOfLongestSubstring(s) {
let mp = new Map()
let l = 0, res = 0;

        for(let r = 0; r < s.length; r++){
            if(mp.has(s[r])){
                l = Math.max(mp.get(s[r]) + 1, l)
            }
            mp.set(s[r], r);
            res = Math.max(res, r - l + 1)
        }
        return res;
    }

### 删除链表的倒数第N个节点
