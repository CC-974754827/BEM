# BEM
块（block）、元素（element）、修饰符（modifier）

这三个部分使用__ 与--连接

> .block__element--modifier{}
* block 代表了更高级别的抽象或组件
* block__element 代表 block 的后代，用于形成一个完整的 block 的整体
* block--modifier代表 block 的不同状态或不同版本

## 原因
css引擎查找样式表，对每条规则都按 **从右到左** 的顺序去匹配

不要让css超过三层

## 使用
使用@at-root（可以使一个或多个规则被限定输出在文档的根层级上,而不是被嵌套在其父选择器下），编译出来的css无任何嵌套
```
.person {
  @at-root #{&}__hand {
    color: red;
    @at-root #{&}--left {
     color: yellow;
    }
  }
}
/*编译出来的css*/
.person__hand {
   color: red;
}
.person__hand--left {
   color: yellow; 
}
```
