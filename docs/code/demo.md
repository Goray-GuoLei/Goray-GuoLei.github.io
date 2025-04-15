1.双指针模板：只有一个输入，从两端开始遍历

```java
public int fn(int[] arr) {
    int left = 0;
    int right = arr.length - 1;
    int ans = 0;

    while (left < right) {
        // 一些根据 letf 和 right 相关的代码补充
        if (CONDITION) {
            left++;
        } else {
            right--;
        }
    }

    return ans;
}

```



2.双指针：有两个输入：两个都需要遍历完

```java
public int fn(int[] arr1, int[] arr2) {
    int i = 0, j = 0, ans = 0;

    while (i < arr1.length && j < arr2.length) {
        // 根据题意补充代码
        if (CONDITION) {
            i++;
        } else {
            j++;
        }
    }

    while (i < arr1.length) {
        // 根据题意补充代码
        i++;
    }

    while (j < arr2.length) {
        // 根据题意补充代码
        j++;
    }

    return ans;
}
```



3.滑动窗口



```java
public int fn(int[] arr) {
    int left = 0, ans = 0, curr = 0;

    for (int right = 0; right < arr.length; right++) {
        // 根据题意补充代码来将 arr[right] 添加到 curr

        while (WINDOW_CONDITION_BROKEN) {
            // 从 curr 中删除 arr[left]
            left++;
        }

        // 更新 ans
    }

    return ans;
}

```



4.构建前缀和

```java
public int[] fn(int[] arr) {
    int[] prefix = new int[arr.length];
    prefix[0] = arr[0];

    for (int i = 1; i < arr.length; i++) {
        prefix[i] = prefix[i - 1] + arr[i];
    }

    return prefix;
}

```



5.高效的字符串创建

```
public String fn(char[] arr) {
    StringBuilder sb = new StringBuilder();
    for (char c: arr) {
        sb.append(c);
    }

    return sb.toString();
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0em40r/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

6.链表：快慢指针



```java
public int fn(ListNode head) {
    ListNode slow = head;
    ListNode fast = head;
    int ans = 0;

    while (fast != null && fast.next != null) {
        // 根据题意补充代码
        slow = slow.next;
        fast = fast.next.next;
    }

    return ans;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0eagws/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```



7.翻转指针

```java
public ListNode fn(ListNode head) {
    ListNode curr = head;
    ListNode prev = null;
    while (curr != null) {
        ListNode nextNode = curr.next;
        curr.next = prev;
        prev = curr;
        curr = nextNode;
    }

    return prev;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0e2qvd/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

8.找到符合确切条件的子数组

```
public int fn(int[] arr, int k) {
    Map<Integer, Integer> counts = new HashMap<>();
    counts.put(0, 1);
    int ans = 0, curr = 0;

    for (int num: arr) {
        // 根据题意补充代码来改变 curr
        ans += counts.getOrDefault(curr - k, 0);
        counts.put(curr, counts.getOrDefault(curr, 0) + 1);
    }

    return ans;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0entnh/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```



9.单调递增栈4



```java
public int fn(int[] arr) {
    Stack<Integer> stack = new Stack<>();
    int ans = 0;

    for (int num: arr) {
        // 对于单调递减的情况，只需将 > 翻转到 <
        while (!stack.empty() && stack.peek() > num) {
            // 根据题意补充代码
            stack.pop();
        }

        stack.push(num);
    }

    return ans;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0evla3/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```



10.二叉树DFS（递归）

```java
public int dfs(TreeNode root) {
    if (root == null) {
        return 0;
    }

    int ans = 0;
    // 根据题意补充代码
    dfs(root.left);
    dfs(root.right);
    return ans;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0ewdmm/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

11.二叉树 DFS(迭代)

```java
public int dfs(TreeNode root) {
    Stack<TreeNode> stack = new Stack<>();
    stack.push(root);
    int ans = 0;

    while (!stack.empty()) {
        TreeNode node = stack.pop();
        // 根据题意补充代码
        if (node.left != null) {
            stack.push(node.left);
        }
        if (node.right != null) {
            stack.push(node.right);
        }
    }

    return ans;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0ednr1/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

```

12.二叉树 BFS

```java
public int fn(TreeNode root) {
    Queue<TreeNode> queue = new LinkedList<>();
    queue.add(root);
    int ans = 0;

    while (!queue.isEmpty()) {
        int currentLength = queue.size();
        // 做一些当前层的操作

        for (int i = 0; i < currentLength; i++) {
            TreeNode node = queue.remove();
            // 根据题意补充代码
            if (node.left != null) {
                queue.add(node.left);
            }
            if (node.right != null) {
                queue.add(node.right);
            }
        }
    }

    return ans;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0e0mo7/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

13图 DFS(递归)

```java
Set<Integer> seen = new HashSet<>();

public int fn(int[][] graph) {
    seen.add(START_NODE);
    return dfs(START_NODE, graph);
}

public int dfs(int node, int[][] graph) {
    int ans = 0;
    // 根据题意补充代码
    for (int neighbor: graph[node]) {
        if (!seen.contains(neighbor)) {
            seen.add(neighbor);
            ans += dfs(neighbor, graph);
        }
    }

    return ans;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0e7oe5/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```



14.图 DFS(迭代)

```java
public int fn(int[][] graph) {
    Stack<Integer> stack = new Stack<>();
    Set<Integer> seen = new HashSet<>();
    stack.push(START_NODE);
    seen.add(START_NODE);
    int ans = 0;

    while (!stack.empty()) {
        int node = stack.pop();
        // 根据题意补充代码
        for (int neighbor: graph[node]) {
            if (!seen.contains(neighbor)) {
                seen.add(neighbor);
                stack.push(neighbor);
            }
        }
    }

    return ans;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0el556/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

```

15.图 BFS

```java
public int fn(int[][] graph) {
    Queue<Integer> queue = new LinkedList<>();
    Set<Integer> seen = new HashSet<>();
    queue.add(START_NODE);
    seen.add(START_NODE);
    int ans = 0;

    while (!queue.isEmpty()) {
        int node = queue.remove();
        // 根据题意补充代码
        for (int neighbor: graph[node]) {
            if (!seen.contains(neighbor)) {
                seen.add(neighbor);
                queue.add(neighbor);
            }
        }
    }

    return ans;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0elfx2/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

```



16 找到堆的前k个元素

```java
public int[] fn(int[] arr, int k) {
    PriorityQueue<Integer> heap = new PriorityQueue<>(CRITERIA);
    for (int num: arr) {
        heap.add(num);
        if (heap.size() > k) {
            heap.remove();
        }
    }

    int[] ans = new int[k];
    for (int i = 0; i < k; i++) {
        ans[i] = heap.remove();
    }

    return ans;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0eiyfc/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

17 二分查找

```java
public int fn(int[] arr, int target) {
    int left = 0;
    int right = arr.length - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) {
            // 根据题意补充代码
            return mid;
        }
        if (arr[mid] > target) {
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }

    // left 是插入点
    return left;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0eusji/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

### 18. 二分查找: 重复元素，最左边的插入点

```java
public int fn(int[] arr, int target) {
    int left = 0;
    int right = arr.length;
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] >= target) {
            right = mid
        } else {
            left = mid + 1;
        }
    }

    return left;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0etkbe/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

### 19. 二分查找: 重复元素，最右边的插入点

```java
public int fn(int[] arr, int target) {
    int left = 0;
    int right = arr.length;
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] > target) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }

    return left;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0e83yg/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

### 20. 二分查找: 贪心问题

寻找最小值

```
public int fn(int[] arr) {
    int left = MINIMUM_POSSIBLE_ANSWER;
    int right = MAXIMUM_POSSIBLE_ANSWER;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (check(mid)) {
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }

    return left;
}

public boolean check(int x) {
    // 这个函数的具体实现取决于问题
    return BOOLEAN;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0e3u1v/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

寻找最大值

```java
public int fn(int[] arr) {
    int left = MINIMUM_POSSIBLE_ANSWER;
    int right = MAXIMUM_POSSIBLE_ANSWER;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (check(mid)) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return right;
}

public boolean check(int x) {
    // 这个函数的具体实现取决于问题
    return BOOLEAN;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0e3u1v/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

### 21. 回溯

```java
public int backtrack(STATE curr, OTHER_ARGUMENTS...) {
    if (BASE_CASE) {
        // 修改答案
        return 0;
    }

    int ans = 0;
    for (ITERATE_OVER_INPUT) {
        // 修改当前状态
        ans += backtrack(curr, OTHER_ARGUMENTS...)
        // 撤消对当前状态的修改
    }
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0eq7sj/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

### 22. 动态规划: 自顶向下法

```java
Map<STATE, Integer> memo = new HashMap<>();

public int fn(int[] arr) {
    return dp(STATE_FOR_WHOLE_INPUT, arr);
}

public int dp(STATE, int[] arr) {
    if (BASE_CASE) {
        return 0;
    }

    if (memo.contains(STATE)) {
        return memo.get(STATE);
    }

    int ans = RECURRENCE_RELATION(STATE);
    memo.put(STATE, ans);
    return ans;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0e6wzt/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

### 23. 构建前缀树（字典树）

```java
// 注意:只有需要在每个节点上存储数据时才需要使用类。
// 否则，您可以只使用哈希映射实现一个前缀树。
class TrieNode {
    // 你可以将数据存储在节点上
    int data;
    Map<Character, TrieNode> children;
    TrieNode() {
        this.children = new HashMap<>();
    }
}

public TrieNode buildTrie(String[] words) {
    TrieNode root = new TrieNode();
    for (String word: words) {
        TrieNode curr = root;
        for (char c: word.toCharArray()) {
            if (!curr.children.containsKey(c)) {
                curr.children.put(c, new TrieNode());
            }

            curr = curr.children.get(c);
        }

        // 这个位置上的 curr 已经有一个完整的单词
        // 如果你愿意，你可以在这里执行更多的操作来给 curr 添加属性
    }

    return root;
}

作者：LeetCode
链接：https://leetcode.cn/leetbook/read/arithmetic-interview-cheat-sheet/0ek2gr/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

