在JavaScript中，call、apply和bind是Function对象自带的三个方法，都是为了改变函数体内部 this 的指向。

> 对于apply和call而言，作用完全一样，只是接受的方式不太一样。call是把参数按顺序传递进去，而apply则是把参数放入数组里面，他们都是立即调用的。
而对于bind则是返回对应的函数，稍后进行调用。

例如：
```js
function printNumber(t) {
    t ? console.log(t) :  console.log(this.x)
}
let obj = {x: 'obj'}
// call
printNumber.call(window, 1) // 1

//apply
printNumber.apply(window, [1])  // 1

/*
bind在MDN的解释为会创建一个新函数称为绑定函数当调用这个绑定函数时，绑定函数会以创建它时，传入bind()方法的第一个参数作为this传入bind()方法的第二个以及以后的参数加上绑定函数运行时本身的参数作为原函数的参数来调用原函数
*/
printNumber.bind(obj)() // obj
```