## 装饰者模式 babel-plugin-transform-decorators-legacy(@withRouter) babel版本<7

@withRouter  装饰器模式的写法写高阶函数  

高阶函数：return 的是一个 component

当 babel 版本 <7时

使用 @withRouter 会报错  

**当 babel 版本 <7时**

需要配置 `babel-plugin-transform-decorators-legacy` 插件

- ```
  $ npm install  babel-plugin-transform-decorators-legacy -D
  ```

- 在 .babelrc  里面配置

  ```javascript
  {
      "plugins": ["transform-decorators-legacy"]
  }
  ```

**当  babel  版本 > 7 时  需要配置**

- `npm install --save-dev @babel/plugin-proposal-decorators `

- 将以下行添加到.babelrc文件中： 

  ```javascript
  "plugins": [
      ["@babel/plugin-proposal-decorators", { "legacy": true }],
    ]
  ```

  ![装饰者模式](C:\Users\51336\Desktop\note-react\img\装饰者模式.png)



#redux



##flux
单向数据流     让任何一个东西变得可跟踪
必须  用一个方法触发状态的改变   在方法之前有一个动作 action
action    =》 方法    =》    state      
方法  一般叫做   dispatch

reducer  必须是一个纯函数  ( pure function )
纯函数：函数的返回值只由参数决定   只要传入的参数一样得到的结果永远一样   纯函数是没有副作用的

## thunk

解决异步的方法

1、`cnpm i redux-thunk -S`

2、

`import {createStore , applyMiddleware , combineReducers } from "redux"`

 `import chunk from "redux-thunk"`

3、在 store 里面的使用

```javascript
const store = createStore(
    //合并  reducer
    combineReducers({
        r1:reducer1,
        r2:reducer2
    })
    applyMiddleware(thunk)
)
```



## 改变 store 里面的数据 Object.assign(）

```javascript
Object.assign({},prevState,{
            age:prevState.age - 1 
        })
```

![redux_Objext.assign()](C:\Users\51336\Desktop\note-react\img\redux_Objext.assign().png)

## combineReducers

combineReducers 辅助函数的作用是，把一个由多个不同 reducer 函数作为 value 的 object，合并成一个最终的 reducer 函数，然后就可以对这个 reducer 调用 createStore。

```javascript
import { createStore, combineReducers } from 'redux';
const ruducers = combineReducers({ 
    r1: reducer, 
    r2: reducer2 
})
const store = createStore(ruducers,composeWithDevTools())
```

## redux DevTools

1、安装 谷歌扩展插件

2、/ /安装redux-devtools-extension的可视化工具。

`import { composeWithDevTools } from 'redux-devtools-extension'`

3、

```javascript
export default  createStore(   
 storeReducer,   
 composeWithDevTools(    )
);
```

## react-redux

## react-id-swiper











