# note-book
Organiza a little knowledge

1. Array.from() : 将伪数组对象或可遍历对象转换为真数组
如果一个对象的所有键名都是正整数或零，并且有 length 属性，那么这个对象就很像数组，称为伪数组。典型的伪数组有函数的 arguments 对象，以及大多数 DOM 元素集，还有字符串。

...
<button>测试1</button>
<br>
<button>测试2</button>
<br>
<button>测试3</button>
<br>
<script type="text/javascript">
let btns = document.getElementsByTagName("button")
console.log("btns",btns);//得到一个伪数组
btns.forEach(item=>console.log(item)) Uncaught TypeError: btns.forEach is not a function
</script>

针对伪数组，没有数组一般方法，直接遍历便会出错,ES6 新增 Array.from()方法来提供一种明确清晰的方式以解决这方面的需求。
Array.from(btns).forEach(item=>console.log(item))将伪数组转换为数组

2. 数组实例的 find() 和 findIndex()

数组实例的 find 方法，用于找出第一个符合条件的数组成员。它的参数是一个回调函数，所有数组成员依次执行该回调函数，直到找出第一个返回值为 true 的成员，然后返回该成员。如果没有符合条件的成员，则返回 undefined。

var arr=[1,8,4,9,7,3,'a','c','b'];
arr.find(n=>n==='a') //"a"

数组实例的 findIndex 方法的用法与 find 方法非常类似，返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回-1。

arr.findIndex(n=>n==='a') //6

关于find() 和some()
如果没有符合条件的成员，find返回undefined,some返回false
查找数组对象中的一个元素是否纯在：
const arr = [{'name':'Tom', 'age': 18},{'name':'marry', 'age': 15}]
arr.find((element,index,array)=>{
  if(element.name==='Tom'){
    console.log(array[index]);
    return ture;
  }
})

参数是一个callback,callback有三个参数，[当前遍历对象,下标,遍历的数组]，some()方法类似
