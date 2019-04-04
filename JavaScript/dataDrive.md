# 数据是如何驱动视图的？

---------------------

现在的前端，我们经常会看到像vue、react、angular这类框架的使用，他们都有一个共同的特点，就是数据驱动视图，但是你知道数据是怎样驱动视图的么，下面我们就来看一看吧！

> 首先，我希望你来想一想，在js中有没有什么方法做到数据改变，就会触发的方法。当然，如果你不知道也没关系，下面我们就来看一看！

现在我们假设，有一个变量，要求输入出生年份，就可以立即显示出年龄age
如：

```javascript
let year = 1995
function getAge(year) {
    return new Date().getFullYear() - year
}
let age = getAge(year)
```

好了，现在我们已经实现了我们的基本要求，当year改变时，然后再调用getAge(year)我们就可以达到我们刚刚的需求了。

> 现在我们来思考一下，能不能做到当year改变，就回自动调用getAge(year)这个函数,来做到age的改变呢。

下面，我们就来介绍今天的主角set/get访问器。

```javascript
let age
let dome = {
    set year(val) {
        age = new Date().getFullYear() - val
        year = val
    },
    get year() {
        return year
    }
}
dome.year = 1995
console.log(age)
```

此刻你会发现，当dome.year改变时，age也会随着改变。
当然，这只是基本的使用方式。这里还有几点get和set使用时注意的：

- get和set是方法，所以可以进行判断
- get是得到，一般要返回。set是设置不用返回
- 如果调用的是对象内部的属性，其命名的约定方式是_year

> 注：第三点，将上面式子中的dome声明year改其内部属性声明

```javascript

let dome = {
    _year: 1995,
    set year(val) {
        age = new Date().getFullYear() - val
        this._year = val
    },
    get year() {
        return this._year
    }
}

```

这里只是简单讲解一下get、set访问器，有想要了解vue双向绑定的朋友请点击[这里](https://www.cnblogs.com/leaf930814/p/6891254.html)