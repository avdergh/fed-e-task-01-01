# 模板一作业回答

## 1、请说出下列最终的执行结果，并解释为什么？
![avatar](https://sls-cloudfunction-ap-guangzhou-code-1252004410.cos.ap-guangzhou.myqcloud.com/%E4%BD%9C%E4%B8%9A1-1.png)
结果为： 9
```
i是用var声明的变量，i此时在全局中声明，作为全局变量，在执行for循环的时候，for循环立马执行，此时i会变成9,当执行a[6]的函数时，打印i即会打印9
```

## 2、请说出下列最终的执行结果，并解析为什么？
![avatar](https://sls-cloudfunction-ap-guangzhou-code-1252004410.cos.ap-guangzhou.myqcloud.com/%E4%BD%9C%E4%B8%9A1-2.png)
结果： 报错
```
用let在块级作用域中声明变量，在变量声明之前访问变量是是不允许的
```


## 3、结合ES6新语法，用最简单的方式找出数组中的最小值？
![avatar](https://sls-cloudfunction-ap-guangzhou-code-1252004410.cos.ap-guangzhou.myqcloud.com/%E4%BD%9C%E4%B8%9A1-3.png)
```
Math.min(...arr)
```

## 4、请详细说明var,let,const三种变量声明的方式之间的区别？
```
    var是ES2015之前声明变量的方式，声明的变量只在全局作用域和函数作用域中，如果在块级作用域中声明变量，变量会提升到上一级的作用域中；另外var声明的变量存在变量提升，及在当前作用域中变量声明之前能够返回该变量，并且返回undefined。 
    let和const是ES2015新增的声明变量的方式，let和const可以在块级作用域中声明变量，不会提升到上一级作用域中；另外也不存在变量提升，如果在声明之前访问变量会运行报错； let和const的区别主要的const声明的变量只读，不能修改。
```

## 5、 请说出下列代码最终的输出结果，并解释为什么？
![avatar](https://sls-cloudfunction-ap-guangzhou-code-1252004410.cos.ap-guangzhou.myqcloud.com/%E4%BD%9C%E4%B8%9A1-5.png)
结果为： 20
```
箭头函数里面的this指的是函数外部的上下文,箭头函数外部的fn函数，fn函数里的上下文对象是obj对象，所有this指向的是obj对象
```

## 6、简述Symbol类型的用途
```
symbol作为一种新的原始数据类型，使用它可以产生独一无二的值；
用途一： 可以作为对象属性，对象的唯一属性；比如 let obj = { [Symbol()] : 123}
用途二： 使数据结构实现可迭代接口，比如Array,Map，Set等都实现了，然后可以用for..of遍历
```

## 7、说说什么是浅拷贝，什么是深拷贝？

```
浅拷贝和深拷贝主要针对的是引用内容，浅拷贝是对内存地址的赋值， 深拷贝是对值得复制
```

## 8、谈谈你是如何理解JS异步编程的，Event Loop 是做什么的，什么是宏任务，什么是微任务？
```
    JS异步编程主要是JS是一门单线程的语言，这里的单线程指的是JS代码执行时在一个单线程中执行，在同一时间只能执行一个任务，且任务是依次往下执行的，但是如果遇到一个任务比较耗时，就会阻塞下面的任务执行，所有JS将任务执行分两种，同步模式执行和异步模式执行；在执行栈中执行代码时，如果遇到异步任务，还是往下执行，异步任务进入Event Table注册回调函数，当异步任务执行完毕，Event Table将注册的回调函数放在 任务队列中；执行栈中的同步任务执行完毕，然后Event Loop查找任务队列中的任务，如果有任务，取出第一个任务放在执行栈中执行；
    Event Loop主要处理任务队列里面的事件消息，当执行栈中的任务执行完毕之后，然后任务队列中有事件消息，Event Loop将任务队列中的第一个事件消息的任务放在执行栈中执行,执行完毕再次查看任务队列的事件消息，有事件消息，将事件回调放在执行栈中执行，一直循环如此；
    异步任务分为宏任务和微任务，宏任务有setImmediate, I/O, UI渲染；微任务有Promise，MutationObserve
```

## 9、将下面异步代码使用Promise改进？
![avatar](https://sls-cloudfunction-ap-guangzhou-code-1252004410.cos.ap-guangzhou.myqcloud.com/%E4%BD%9C%E4%B8%9A1-9.png)
``` JavaScript
function sleep(time, text) {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve(text)
        }, time)
    })
}
sleep(30, `hellolagouI U`).then((result) => {
    console.log(result)
})
```

## 10、请简述TypeScript与JavaScript之间的关系？
```
TypeScript是JavaScript的超集，也就是说TypeScript是在JavaScript基础之前的编程语言，其主要在JavaScript上增强了类型系统和面向对象编程；TypeScript需要经过编译成JavaScript才能运行；
```



## 11、请谈谈你所认为的TypeScript的优缺点？
```
JavaScript是一门弱类型动态类型的脚本语言，在声明变量和给变量赋值灵活；TypeScript是在JavaScript的基础上加强的编程语言，主要加强了类型系统和面向对象编程；
优点：在处理大型的一直迭代的前端项目的时候，由于强类型的约束，增加系统的稳定性和可靠性及代码的可读性；但是对于小型的前端项目没有显著的优点。

缺点：不够灵活，需要定义每一个类型，增加了工作量，然后只能编译成js才能运行。

```