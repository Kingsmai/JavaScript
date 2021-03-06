### 关于数组的常用API

> 检测数组

```
// 1. if(value instanceof Array) {}, 并不推荐,存在跨页面问题
// 2. Array.isArray(value) // IE9+、Firefox4+、Safiri5+、Opera10.5+、Chrome
// 3. if(Array.prototype.toString.call(arr) === '[object Array]')
```

> 转换方法

```
1. toString()
2. valueOf() 调用这个返回的还是数组
	alert(colors.valueOf()); // 由于alert要接受字符串参数，所有数组会在后台调用toString()方法
3. toLocaleString(); 如果数组调用这个方法，调用的是数组每一项的toLocalString()方法, 和其他方法一样，会创建一个字符串，数组项以逗号分隔
4. join(",") 数组项会以传入的参数分隔
```

> 栈方法

```
1. push(); // 向数组添加元素, 传入参数可以是多个，返回值是数值，传入几个就返回几。
2. pop(); // 取得数组最后一项, 返回被移除的项
```

> 队列方法

```
1. shift() // shift的意思是改变、去掉, 取得第一项，返回被取得的项
2. unshif() // 从数组前端插入项，返回项的个数
```

> 重排序方法

```
1. reverse() // 翻转数组的顺序
2. sort() // 升序排序，sort()会调用每个数组项的toString()转型方法
		  // 然后比较得到的字符串。即使传入的是数值，比较的仍旧是字符串
		  // 因此sort()方法接受一个比较函数,比较函数接受两个参数 
		  // 如果第一个参数在第二个参数前返回一个负数。

// 这个比较函数可以适用于大部分的数据类型
function compare(value1, value2) {
	if(value1 < value2) {
		return -1;
	} else if(value1 > value2) {
		return 1;
	} else {
		return 0;
	}
} 

// 对于数值类型或者其valueOf()方法会返回数值类型的对象类型
function compare(value1, value2) {
	return value1 - value2;
}
```

> 操作方法

```	
1. concat() 
	// 如果没有传入参数，那么是复制当前数组并返回副本
	// 如果传入的是一个或多个数组，则会将这些数组的每一项都添加到数组里
	// 如果传入的不是数组，这些值会被简单地添加到结果数组的末尾。
	// 最终会返回一个新数组，原来的数组保持不变
2. slice()
	// 它能够基于当前数组的一项或多项创建一个新数组
	// 它不会影响原数组，可以接受一或两个参数
	// 如果传入一个参数，会返回当前位置到数组末尾的所有项
	// 如果传入两个参数，会返回当前位置到数组末尾位置(除了最后一个)中间的所有项
3. splice()	
	// 删除, 2个参数，第一个是从哪一项开始，第二项是要删除的个数
	// 插入，3个参数及以上, 第一个是从哪一项开始插入，第二项为0，后面表示要插入的项
	// 替换，3个参数及以上，第一个是从哪一项开始插入，第二项是要删除的项数，后面表示要替换的项，可以与删除的项数不一样。
```

> 位置方法

```
// IE9+才支持
1. indexOf() 接受一个或两个参数，如果只有一个参数，表示在数组里查找某一项的位置, 如果存在，返回下标，若不存在，返回-1。如果是两个参数，第二个参数表示从哪个位置开始查找。
2. lastIndexOf()同indexOf，只不过是从数组末尾开始查询。
```

> 迭代方法

```
// IE9+才支持
// 说明：每个方法接受两个参数，一个是在每个数组项上运行的函数和（可选的）运行该函数的作用域(改变this的值), 运行的函数接受3个参数，分别是(item, index, arrry)
1. every() // all return true --> return true
2. filter() // 返会该函数会返回true组成的数组 
3. forEach() // 每个项都执行函数，不返回值
4. map() // 返回每次函数调用的结果组成的数组
5. some() // some return true --> return true
```

> 归并方法

```
// IE9+才支持
// 说明：每个方法接受两个参数，一个是在每个数组项上调用的函数和（可选的）作为归并基础的初始值。传给reduce()的函数接受四个参数，分别是(前一个值，当前值，项的索引，数组对象),这个函数的任何返回值都会作为第一个参数传递并且自动传给下一项。
1. reduce() 
2. reduceRight()

var values = [1, 2, 3, 4, 5];
var sum = values.reduce(function(prev, cur, index, array) {
	return prev + cur;	
});
console.log(sum); // 15
```







