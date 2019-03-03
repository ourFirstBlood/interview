### 什么是MVVM？
有兴趣的同学可以去看一下[廖雪峰的网站](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/001475449022563a6591e6373324d1abd93e0e3fa04397f000)，这里只是简单的说一下！

MVVM：简单来说就是Module-View-ViewModule的简写。

MVVM最早由微软提出来，它借鉴了桌面应用程序的MVC思想，在前端页面中，把Model用纯JavaScript对象表示，View负责显示，两者做到了最大限度的分离。
把Model和View关联起来的就是ViewModel。ViewModel负责把Model的数据同步到View显示出来，还负责把View的修改同步回Model。
ViewModel如何编写？需要用JavaScript编写一个通用的ViewModel，这样，就可以复用整个MVVM模型了。

### MVVM有什么优点？

MVVM模式和MVC模式一样，主要目的是为了分离视图(view)和模型(module)，有几大优点：

- 低耦合：视图可以独立Module变化和修改，一个ViewModule可以绑定到不同的View上，当View变化的时候Module可以不变，当Module变化的时候View也可以不变。
- 可重用性：你可以把视图逻辑放在一个ViewModule中，让很多的View重用这段视图逻辑。
- 独立开发：开发人员可以专注于业务逻辑和数据的开发（ViewModel），设计人员可以专注于页面设计，使用Expression Blend可以很容易设计界面并生成xaml代码。
- 可测试：界面素来是比较难于测试的，而现在测试可以针对ViewModel来写。