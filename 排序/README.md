### 排序算法

### 归并
[912.排序数组](https://leetcode-cn.com/problems/sort-an-array/)

#### 思路
1. 将数组进行切割
   1. 把数组按照中位数拆分成左右两部分
   2. 把左右两部分切割成最小单位
2. 合并排序
   1. 使用一个变量存放排序后的数组
   2. 进行大小对比排序+合并
  

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortArray = function(nums) {
    
    const sort = arr => {
        const n = arr.length
        if (n === 1) {
            return arr
        }
        const mid = parseInt(n/2)
        const left = arr.slice(0,mid)
        const right = arr.slice(mid)
        return merge(sort(left),sort(right))
    }
    const merge = (l,r) => {
        let p1 = 0,p2 = 0,n1 = l.length,n2 = r.length,i = 0
        const res = []
        while(p1<n1&&p2<n2) {
            if (l[p1]<r[p2]) {
                res[i++] = l[p1++]
            } else {
                res[i++] = r[p2++]
            }
        }
        while(p1< n1) {
            res[i++] = l[p1++]
        }
        while(p2< n2) {
            res[i++] = r[p2++]
        }
        return res
    }
    return sort(nums)
};
```