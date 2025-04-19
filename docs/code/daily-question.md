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