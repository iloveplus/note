## 数组扁平化

var arr=[1,[2,3],4,[5,6,[7,8,[9]]]]

解法1：
```
arr.flat(Infinity)
```

解法2：
```
arr.join(',').split(',')
```

解法3：
```
JSON.stringify(arr).replace(/\[|\]/g, '').split(',')
```

解法4：
```
function flatArr(arr) {
	return arr.reduce((pre, cur) => {
		return pre.concat(Array.isArray(cur) ? flatArr(cur) : cur)
	}, [])
}
flatArr(arr)
```

解法5：
```
while(arr.some(Array.isArray)) {
	arr = [].concat(...arr)
}
```
