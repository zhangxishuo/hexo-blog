---
title: AngularJS 单元测试
date: 2018-02-04 21:49:49
categories: AngularJS
tags:
- javascript
- 单元测试
---

写了前台的过滤器，引入了`AngularJS`的单元测试，最初感觉`Jasmine`的语法怎么看起来这么复杂，当真正理解时，发现过滤器的单元测试其实很简单。

过滤器相比`AngularJS`中的指令、控制器等的测试还是相对简单的，作为过滤器，功能就是对某个对象进行过滤，然后过滤为一个新的对象。

所以，测试过滤器，我们只需要给一个输入，然后断言它的输出是什么即可。

<!-- more -->

**测试功能**

待测试过滤器为器具使用状态过滤器。

前后台定义器具有如下5种状态：

```javascript
{id: -2, value: '被退回', style: 'danger'},
{id: -1, value: '未备案', style: 'info'},
{id: 0, value: '正常', style: 'success'},
{id: 1, value: '停用', style: 'warning'},
{id: 2, value: '报废', style: 'warning2'}
```

**分析**

如果状态为被退回或未备案，返回空字符串。

如果状态为正常、停用、报废，返回一个带有样式的`span`标签，如果该器具有器具状态变更记录，则该`span`可点击，同时显示变更记录，否则`span`不可点击。

过滤器，无所谓输入与输出，根据该过滤器的功能，我们可以很容易地分析出输入与输出。

**Jasmine语法简介**

`Jasmine`使用`describe`描述一个测试集，参数`String`用于描述这个测试集，参数`function`中的用来写我们的测试用例。

`it`表示一个测试用例，与`describe`类似，参数为测试用例描述和执行方法。

`expect`表示一个断言，类似于我们在`SpringBoot`使用的`AssertThat`，我断定这个的值是什么。

