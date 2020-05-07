## 度度熊想去商场买一顶帽子，商场里有N顶帽子，有些帽子的价格可能相同。度度熊想买一顶价格第三便宜的帽子，问第三便宜的帽子价格是多少？
测试数据：
```js
var arr=[10, 25, 50, 10, 20, 80, 30, 30, 40, 90];
```

> 解法一
```js
data.filter((item, index, self) => self.indexOf(item) === index).sort()[2]
```

> 解法二
```js
function fun(arr,index){
    var min=Math.min.apply(this,arr);
    if(index<=0){
        return min;
    }else{
        arr=arr.filter((item)=>{return item!=min;});
        if(arr.length==0){
            return min;
        }
        return fun(arr,--index)
    }
}
```
