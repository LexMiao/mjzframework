###mjfn.js 前端框架说明

>用户注意：选择器仅仅只可以在前端使用，此框架不建议在后端：node.js内使用。本框架效仿jquery框架，但相比jquery更加轻量，会做一些持续的更新！并且添加了一些通用的模块，大大方便前端工程师的编写。
本框架暂不适配IE8！！！！

###本框架使用链式调用，仅仅只有以下方法不支持。

>remove/getClass/ele_W_H/body_W_H/click／pagination/Time、arrChan、strChan、obj、对象下的方法／和抛错方法

引入本框架只运用一个全局变量：MjFn变量，在变量内有的原型方法内挂载着所有的操作方法。并且运用无new创建，因此，如果要使用，请在\<script\>标签内嵌入以下的代码：

```js
MjFn('.className');       //example,括号内的内容是css选择器的格式
```

可以对取出的元素进行筛选，因此就诞生了：

```js
MjFn('.className').first();         //内的第一个元素
MjFn('.className').end();           //内的最后一个元素
MjFn('.className').num(num);        //传入的参数为这些内容内的第几个
```

css方法：传入style，两种形式

```js
MjFn('.className').css('background-color','#ABC');      //传入两个参数
MjFn('.className').css({
    'background-color':'#ABC',
    'border-radius':'10px',
    'height':'50px',
    });     //传入一个json对象
```


removeClass / addClass / replaceClass  (添加、删除和替代节点的class)

```js
MjFn('.className').addClass('className');
MjFn('.className').removeClass('className');
MjFn('.className').replaceClass('className');
```

getClass：获取元素类名
 
```js
MjFn('.className').getClass();
```

可以ele_W_H清空html标签内的所有子节点（clear）

```js
MjFn('.className').clear();
```

清空这个节点（包括其子节点）

```js
MjFn('.className').remove();
```

返回可见高度：（分为元素和body两个）    the end of invocation chaining

```js
MjFn('.className').ele_W_H();       //元素可见的宽和高，返回一个array，arr[0]是宽，arr[1]是高
MjFn('.className').body_W_H();      //页面可见的宽和高，返回一个array，arr[0]是宽，arr[1]是高
```

addHTML：为元素添加子节点

```js
MjFn('.className').addHTML('<a>我是子节点</a>');
```

替换和添加内容（chanText、addText）
>强烈建议添加内容使用这个，而不是addHTML：这两个方法在添加内容之前，会对html代码做出转译！对其不执行html处理，把它当成字符串输出。

```js
MjFn('.className').chanText(str);       //替换字符串
MjFn('.className').addText(str);        //在原有的基础上添加内容
```

click方法：点击事件

```js
MjFn('.className').click(function(e) {      //e为点击事件！
        expression
    });
```

Time对象：获取事件

```js
MjFn().Time.DateFac();      //统一工厂方法：DateFac方法  [几年几月几号,几时几分几秒]
```

pagination方法：传入URL、本页页数、总页数(>7页显示7页，<7页显示total)

```js
MjFn('#page').pagination('URL', 5, 12);     //下面附图，配合framework.css工作效果更佳！
```

ajax方法(传入json参数、URL地址)：

```js
MjFn().ajax('http://localhost:8080/ajax/server1.php', 'post', function(data) {
    console.log(data);
}, {
    'POSTval': 'val',
});
```

