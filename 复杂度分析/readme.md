# 算法的时间复杂度和空间复杂度  
## 必要性  
复杂度分析是整个算法学习的精髓  
事后统计的局限很大，测试的结果受到环境(处理器)和数据规模的影响比较大(规模太小结果可能无法反映性能)  

## 大 O 复杂度表示法  
不用具体的测试数据就可以估计算法的执行效率  
```js
function sum(arr) {
  let result = 0
  let len = arr.length
  for(let i = 0; i < len; i++) {
    result += arr[i]
  }
  return result
}
```
1. 第 2、3 行代码分别会被执行 1 次  
2. 循环体内的 result += arr[i] 会被执行 n 次(数组长度)  
3. 循环中的 let i = 0 会被执行一次  
4. 循环的判断 i < len 会被执行 n + 1 次  
5. i++ 会被执行 n 次  
总执行时间：T(n) = 1 + 1 + n + 1 + (n + 1) + n = 3n + 4  
```js
function sum(arr) {
  let result = 0
  let outLen = arr.length
  for(let i = 0; i < outLen; i++) {
    let inLen = arr[i].length
    for(let j = 0; j < inLen; j++) {
      result += arr[i][j]
    }
  }
  return result
}
```
1. 第 2、3 行代码分别会被执行 1 次  
2. let i = 0 执行 1 次  
3. i < outLen 执行 n + 1 次  
4. i++ 执行 n 次  
5. let inLen = arr[i].length 执行 n 次  
6. let j = 0 执行 n 次  
7. j < inLen 执行 n * (n + 1) 次  
8. j++ 执行 n * n 次  
9. result += arr[i][j] 执行 n * n 次  
同样的计算方式 T(n) = 1 + 1 + 1 + (n + 1) + n + n + n * (n + 1) + n * n + n * n = 3n² + 4n + 4  
