---
2025-04-19  统计公平数对的数目
---
题目名称：

给你一个下标从 0 开始、长度为 n 的整数数组 nums ，和两个整数 lower 和 upper ，返回 公平数对的数目 。

如果 (i, j) 数对满足以下情况，则认为它是一个 公平数对 ：

0 <= i < j < n，且
lower <= nums[i] + nums[j] <= upper


示例 1：

输入：nums = [0,1,7,4,4,5], lower = 3, upper = 6
输出：6
解释：共计 6 个公平数对：(0,3)、(0,4)、(0,5)、(1,3)、(1,4) 和 (1,5) 。
示例 2：

输入：nums = [1,7,9,2,5], lower = 11, upper = 11
输出：1
解释：只有单个公平数对：(2,3) 。


提示：

1 <= nums.length <= 10^5
nums.length == n
-109 <= nums[i] <= 10^9
-109 <= lower <= upper <= 10^9


解题思路：
其实下标的顺序并不重要

```java

package org.example.Year2025.M04_April;

import java.util.Arrays;
/**
 * @ClassName: Day18Medium
 * @Description: 统计公平数对的数目
 * @TODO:
 * @Author 路遥马急
 * @Create 2025/4/19 12:01
 * @Version 1.0
 */


public class Day18Medium {
    public long countFairPairs(int[] nums, int lower, int upper) {
        long res=0;
        Arrays.sort(nums);
        int n=nums.length;
        int p=0;
        int q=nums.length-1;
        while(p<q){
            if(nums[p]+nums[q]<lower){
                p++;
            }else if(nums[p]+nums[q]>upper){
                q--;
            }else{
                res++;
                for(int left=p+1;left<q;left++){
                    if(nums[left]+nums[q]>upper){
                        break;
                    }
                    res++;
                }
                for(int right=q-1;right>p;right--){
                    if(nums[right]+nums[p]<lower){
                        break;
                    }
                    res++;
                }
                p++;
                q--;
            }
        }
        return res;

    }
}
```


---
2025-04-20  森林中的兔子
---
森林中有未知数量的兔子。提问其中若干只兔子 "还有多少只兔子与你（指被提问的兔子）颜色相同?" ，将答案收集到一个整数数组 answers 中，其中 answers[i] 是第 i 只兔子的回答。

给你数组 answers ，返回森林中兔子的最少数量。

 

示例 1：

输入：answers = [1,1,2]
输出：5
解释：
两只回答了 "1" 的兔子可能有相同的颜色，设为红色。 
之后回答了 "2" 的兔子不会是红色，否则他们的回答会相互矛盾。
设回答了 "2" 的兔子为蓝色。 
此外，森林中还应有另外 2 只蓝色兔子的回答没有包含在数组中。 
因此森林中兔子的最少数量是 5 只：3 只回答的和 2 只没有回答的。
示例 2：

输入：answers = [10,10,10]
输出：11
 

提示：

1 <= answers.length <= 1000
0 <= answers[i] < 1000

```java
package org.example.Year2025.M04_April;

import java.util.*;

/**
 * @ClassName: Day19Medium
 * @Description:
 * @TODO:
 * @Author 路遥马急
 * @Create 2025/4/20 8:16
 * @Version 1.0
 */
public class Day19Medium {
    //哈希的思想,记录answer值相同的元素然后进行编队成为组
    public int numRabbits(int[] answers) {
        //Map<Integer,Integer> cnt=new HashMap<>();
        int []cnt=new int [10001];//元素数量只有1000可以考虑使用数组实现hash的思想，提升性能
        int res=0;
        for(int i=0;i<answers.length;i++){//
            if(answers[i]==0){//自己独立成为一类
                res+=1;
            }else {
                //更新类型和数量
                cnt[answers[i]]++;
                //cnt.put(answers[i],cnt.getOrDefault(answers[i],0)+1);
            }
        }
        // for(Map.Entry<Integer,Integer> entry: cnt.entrySet()){
        //     int num=entry.getKey()+1;
        //     int count=entry.getValue();
        //     int tmp=count%num;
        //     int sum=tmp==0? count:count+(num-tmp);
        //     res+=sum;
        // }
        for(int i=0;i<cnt.length;i++){
            if(cnt[i]!=0){//计算这个不同类型的数量，进行编队
                int num=i+1;
                int tmp=cnt[i]%num;
                int sum=tmp==0? cnt[i]:cnt[i]+(num-tmp);
                res+=sum;
            }
        }
        return res;
    }
}
```

---
2025-04-21  统计隐藏数组数目
---

给你一个下标从 0 开始且长度为 n 的整数数组 differences ，它表示一个长度为 n + 1 的 隐藏 数组 相邻 元素之间的 差值 。更正式的表述为：我们将隐藏数组记作 hidden ，那么 differences[i] = hidden[i + 1] - hidden[i] 。

同时给你两个整数 lower 和 upper ，它们表示隐藏数组中所有数字的值都在 闭 区间 [lower, upper] 之间。

比方说，differences = [1, -3, 4] ，lower = 1 ，upper = 6 ，那么隐藏数组是一个长度为 4 且所有值都在 1 和 6 （包含两者）之间的数组。
[3, 4, 1, 5] 和 [4, 5, 2, 6] 都是符合要求的隐藏数组。
[5, 6, 3, 7] 不符合要求，因为它包含大于 6 的元素。
[1, 2, 3, 4] 不符合要求，因为相邻元素的差值不符合给定数据。
请你返回 符合 要求的隐藏数组的数目。如果没有符合要求的隐藏数组，请返回 0 。

 

示例 1：

输入：differences = [1,-3,4], lower = 1, upper = 6
输出：2
解释：符合要求的隐藏数组为：
- [3, 4, 1, 5]
- [4, 5, 2, 6]
所以返回 2 。
示例 2：

输入：differences = [3,-4,5,1,-2], lower = -4, upper = 5
输出：4
解释：符合要求的隐藏数组为：
- [-3, 0, -4, 1, 2, 0]
- [-2, 1, -3, 2, 3, 1]
- [-1, 2, -2, 3, 4, 2]
- [0, 3, -1, 4, 5, 3]
所以返回 4 。
示例 3：

输入：differences = [4,-7,2], lower = 3, upper = 6
输出：0
解释：没有符合要求的隐藏数组，所以返回 0 。
 

提示：

n == differences.length
1 <= n <= 105
-10^5 <= differences[i] <= 10^5
-10^5 <= lower <= upper <= 10^5

```java
package org.example.Year2025.M04_April;

/**
 * @ClassName: Day21Medium
 * @Description:
 * @TODO:
 * @Author 路遥马急
 * @Create 2025/4/21 10:09
 * @Version 1.0
 */
public class Day21Medium {
    

    //确定数组的范围
    public int numberOfArrays(int[] differences, int lower, int upper) {
        int len=upper-lower+1;
        int max=0;//确定最大值
        int min=0;//确定最小值
        int p=0;
        for(int i=0;i<differences.length;i++){
            p=p+differences[i];
            max=Math.max(max,p);
            min=Math.min(min,p);
            if(max-min+1>len){//一种特殊情况，有的样例会造成max,min叠加溢出
                return 0;
            }
        }
        int range=max-min+1;//隐藏数组的数值范围

        if(len<range){
            return 0;
        }else{
            return len-range+1;
        }
    }
}
```

---
2025-04-26  Sat 统计隐藏数组数目
---