![img.png](img.png)

# 请你实现一下这个 obj 对象,使得最后的输出结果为 10 const res = obj[1][2][3] + 4

问题：*请你实现一下这个 obj 对象,使得最后的输出结果为 10 (1+2+3+4)*

```JavaScript
const res = obj[1][2][3] + 4
```

需要实现proxy，可以获取propKey的值

```JavaScript
const obj = new Proxy({},{
    get(target, prop, receiver) {
        return prop
    }
})
 console.log(obj[1])
```

但是当实现obj[1][2]时会报错，识别为undefined

修改proxy为递归

```JavaScript
const addProxy = (value = 0)=>{
    return new Proxy({},{
        get(target,propKey){
            if(propKey===Symbol.toPrimitive){
                return ()=>value
            }
            return  addProxy(value+Number(propKey))
        },
    })
}
const obj=addProxy()
const res = obj[1][2][3]+4
console.log(res);
```

最后将[1][2][3]的结果转为了+4，symbol.toPrimitive会默认转换为原始数据类型，而在右边的数字是number类型，因此会呈现为6+4=10，单独呈现不改变类型。

当需要单独呈现时，可以改为apply陷阱，代理函数对象，

```JavaScript
const addProxy = (value = 0)=>{
    return new Proxy(function(){},{
        get(target,propKey){
            if(propKey===Symbol.toPrimitive){
                return ()=>value
            }
            return  addProxy(value+Number(propKey))
        },
        apply(target, thisArg, argArray) {
            return value
        }
    })
}
const obj=addProxy()
const res = obj[1][2][3]()+4
console.log(res);
```

参考：[一道字节面试题，不会的还有太多](https://juejin.cn/post/7352018939906424884)
