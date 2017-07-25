# sort[排序算法]   
## [排序算法动画演示](https://visualgo.net/en/sorting)  

+ [简](http://www.jianshu.com/p/7e6589306a27)   
+ [知](https://zhuanlan.zhihu.com/p/27095748)

## 1.冒泡排序[bubble]：    
两两比较，大者后放
```
function sort(arrInput){

      var arrOutput = arrInput.splice(0),
          len = arrOutput.length,
          exchange,
          transit;
          
      for (var i=1; i<len; i++){   //两两比较，只需要length-1次循环，i=1
        exchange = false
        for (var j=0; j<len-i; j++){  
        //每次比较完之后，下次比较就会少一次，所以j=length-i(正好也规避了j+1不存在的情况)
          if (arrOutput[j]>arrOutput[j+1]){
            transit = arrOutput[j]
            arrOutput[j] = arrOutput[j+1]
            arrOutput[j+1] = transit
            exchange = true
          }  
        }
        if (!exchange){
            return arrOutput  // 当没有出现交换时，说明已经排好序，此时直接结束循环操作
        }
      }
      return arrOutput
    }
console.log(sort([4,7,3,9,1,12,74,34,5,78]))
```

## 2.选择排序[selection]:
一多比较，一轮过后选出最小值，放在第一位置
```
  function sort(arr){
    var newArr = arr.slice(0)
    var len = newArr.length,
              k, transit
    for (var i=0; i<len-1; i++){
      k = i  // 每次循环开始指定循环的第一个变量为最小值
      for (var j=i+1; j<len; j++){
        if (newArr[j]<newArr[k]){
          k = j   // 当后面的数小于指定的最小值时，记录下它的位置k
        }
      }
      if (i!==k){  // 进行数值交换
        transit = newArr[k]
        newArr[k] = newArr[i]
        newArr[i] = transit
      }
    }
    return newArr 
  }
console.log(sort([4,6,2,7,1,100,78]))
```
## 3.插入排序[insert]:   
从第一个数字为一个数组（插入的时候已排好序），后面依次比较插入的合适的位置
```
// 插入排序 从下标1开始每增1项排序一次，越往后遍历次数越多
function sort1(array) {
  var newArr = array.slice(0)
  var len = array.length
  var transit, j
  for (var i=1; i<len; i++){
      transit = newArr[i]  //  待插入的值
      j = i-1  //右侧开始数值
    while (j>=0 && transit<newArr[j]){  //比较两个值的大小，如果待插入  的值小于数组中的值，将数组中的值位置前移
      newArr[j+1] = newArr[j]
      j--  //  不断向左比较数组中的值
    }
    newArr[j+1] = transit  //确定下最终的位置后插入空缺newArr[j=1]的值
  }
  return newArr
}
console.log(sort1([3,5,7,1,45,34,20]))
```
## 4.归并排序[merge]  
left --> right (从单个数值，到多个数组都执行这个顺序)

```
    var arr = [3,62,23,45,6,10,15,8]
    function sort(arr){

      var result = arr.slice()

      // 递归分组比较
      function subgroup(arr){
        var len = arr.length
        var mid = Math.floor(len*0.5)
        var left = arr.slice(0,mid)
        var right = arr.slice(mid)
        if (len===1){
          return arr
        }
        return merge(subgroup(left), subgroup(right))
      }

      // 比较插入
      function merge(left, right){
        var result = []
        while(left.length || right.length){
          if (left.length  && right.length){
            if (left[0]<right[0]){
              result.push(left.shift())
            }else{
              result.push(right.shift())
            }
          }else if(left.length){
              result.push(left.shift())
          }else{
            result.push(right.shift())
          }
        }
        return result
      }

      return subgroup(result)
    }


console.log(sort(arr))
```
