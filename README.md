# sort[排序算法]   
## [排序算法动画演示](https://visualgo.net/en/sorting)  
## 1.冒泡排序[bubble]：  
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

## 选择排序[selection]
```

```
