trainning by wenxu

## variables
is a containner, property:

    * value
    * type
    * scope

#### type

> value&reference and 可变/不可变要做区分  
> in python, number is also a object , a reference type, 但是不可变, 感觉上是value type, but not. This is for performance and implement.

* value type: contains the data
    * number
    * string...
* reference type: contains a pointer to anther memory location where is data
    * hash
    * array
    * list

#### scope & context
function has sperate scope, so we should trans reference type variable.

> block is a scope?
> java, c is
> python, js is not

    g = 1                                                                           def foo():
        print g  # 本地变量,在函数内任意位置可见, 但是在print的时候g尚未赋值.
        g = 2

    foo() 

**UnboundLocalError: local variable 'g' referenced before assignment**

in python: default scope is local  
in js: default scope is global

#### compare (==, ===, __eq__)
* in js: `new Class` alwarys alloc new memory.  
* ==: compare variable address.  
* === compare variables and no converstion.  
* \__eq__: 重载操作符, 很优雅, 但难于理解.

#### type converstion
强类型 or 弱类型, 是否自动转换.

    // cond should be a boolean, if type of cond is not boolean, cond will be converstion automaticly.
    if (cond) {  
    }


## function
* an excutable object.
    
        class C():
            """Docstring for C """

            def __init__(self):
                """@todo: to be defined """
                pass

            def __call__(self):
                print 'hello'

        a = C()
        a()

* as a parameter, first class object.
* as a return.

## closure
> 穷人的面向对象  
> 实现了动态作用域,  逃避词法作用域  
> **警惕大量closure对内存浪费**  
> python中装饰器工作的必要条件, 装饰器类似于js中的callback, 是一个中间层.

    def foo(n):
        def bar(m):
            print n + m
        return bar

    f = foo(100) # f(1) --> 101
    f1 = foo(1) # f1(1) --> 2

只被调用一次的匿名函数, 通常用于创建作用域. js, python中没有块作用域, so...

    function foo() {
        var bars = [];
        for (var index = 0; index < 10; index += 1) {
            (function () {  // 多一层闭包用以保存index
                var local = index;
                bars.push(function () {console.log(local)});
            })();
        }
        return bars;
    }

    var bars = foo();
    for (var index = 0; index < 10; index += 1) {
        bars[index]();
    }
