# sort[排序算法]  
---  
1. 冒泡排序：  
```
function sort(arrInput){
      var arrOutput = arrInput.splice(0)
      var len = arrOutput.length
      var exchange
      for (var i=1; i<len; i++){   //两两比较，只需要length-1次循环，i=1
        exchange = false
        for (var j=0; j<len-i; j++){  //每次比较完之后，下次比较就会少一次，所以j=length-i(正好也规避了j+1不存在的情况)
          if (arrOutput[j]>arrOutput[j+1]){
            var transit;
            transit = arrOutput[j]
            arrOutput[j] = arrOutput[j+1]
            arrOutput[j+1] = transit
            exchange = true
          }  
        }
        if (!exchange){
            return arrOutput
        }
      }
      return arrOutput
    }
console.log(sort([4,7,3,9,1,12,74,34,5,78]))
  </script>
```
