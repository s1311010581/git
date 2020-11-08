java引擎

1.从网络、浏览器缓存或 service worker **加载脚本**为 UTF-16 编码的字节流

2.将字节流解析成 **token**

3.将 token 解析成**抽象语法树（abstract syntax tree，AST）**

4.将抽象语法树**解释**成**字节码***

5.（可能）将字节码与类型反馈**编译**成**高度优化过的机器码**

语法环境3种组件

![image-20201102123817057](C:\Users\41359\AppData\Roaming\Typora\typora-user-images\image-20201102123817057.png)

执行上下文和执行线

环境示例:

let x = 10;

let y = 20;


 function foo(z) {

 let x = 100;

 return x + y + z;

}


 foo(30); // 150

![image-20201102124418571](C:\Users\41359\AppData\Roaming\Typora\typora-user-images\image-20201102124418571.png)



函数提升:

使用函数声明定义的函数被自动提升，也就是说它们可以在它们被定义的位置之前被调用。例如，在如下的代码中，函数hoist()可以在实际定义它的位置之前调用

// 函数在代码的开始被调用

hoist();


 // ...

// ... 

// ...


 // 函数定义位于代码的末尾

function hoist(){

 console.log('提升我！'); 

} 

注：⦿变量提升只适用于用 var 声明的变量。 const、let 声明的变量不提升！

⦿ 暂时性死区

变量提升

⦿ 函数表达式与变量提升的方式相似！也就是说，如果函数表达式是用 var 声明的，那么声明会被提升，不过实际的函数是不会提升的！



背后:

⦿ 在执行代码之前，将函数和变量存储在内存中以用于执行上下文。这称为变量提升（hoisting）。

⦿ 函数被存储为一个对整个函数的引用，用var关键字声明的变量的值为undefined，而用let和const关键字声明的变量未被初始化。



⦿三种函数调用形式

⦿ func(p1, p2)  à func.call(undefined, p1, p2)

⦿ obj.child.method(p1,p2) à obj.child.method.call(obj.child, p1, p2)

⦿ func.call(context, p1, p2)

⦿ 本质上都是 func.call(context, p1, p2)，其它两种都是语法糖。 

⦿ 如果传入的 context 不是一个对象，那么全局对象就是默认的 context。****

