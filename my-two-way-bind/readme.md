# two-way-bind 双向绑定

## 主要角色

### Dep 类解读

**if(Dep.target)的判断在代码是有效**
从以下Dep的类结构中可以看出  target是一个静态变量，属于类，不属于 `new Dep()`产生的实例，类似于一个全局变量。所以可以用来做 `if(Dep.target)`的全局方式的判断

Dep 类结构

```javascript
    Dep: ƒ Dep()
    target: null
    arguments: null
    caller: null
    length: 0
    name: "Dep"
    prototype:
    addSub: ƒ (sub)
    notify: ƒ ()
    [[Prototype]]: Object
```

var  a = new Dep();
a的结构

```javascript
a: Dep
// 并没有target属性，因为属于Dep类
    subs: Array(0)
    length: 0
    [[Prototype]]: Array(0)
    [[Prototype]]: Object
    addSub: ƒ (sub)
    notify: ƒ ()
    [[Prototype]]: Object
```