Redux 只是一个用来管理state并进行概念上的约束的这么一个类库，实际开发过程中还会配合 UI 绑定库 react-redux
===
>## Redux一共只有5个API，通过这5个API进行 state管理机制的扩展和约束
>* createStore(reducer,[preloadedState]、[enhancer])
>* combineReducers(reducers)
>* applyMiddleware(...middlewares)
>* bindActionCreators(actionCreateors,dispatch)
>* compose(...function/')

>## stroe API
>* getState
>* dispatch
>* subscribe
>* getReducer
>* replaceReducer(nextReducer)

>## [题外] umd 的含义是通用模块规范，是对 AMD CommonJS的一种兼容性写法
    (function (root, factory) {
        if (typeof define === 'function' && define.amd) {
            // AMD
            define(['jquery'], factory);
        } else if (typeof exports === 'object') {
            // Node, CommonJS-like
            module.exports = factory(require('jquery'));
        } else {
            // Browser globals (root is window)
            root.returnExports = factory(root.jQuery);
        }
    }(this, function ($) {
        //    methods
        function myFunc(){};

        //    exposed public method
        return myFunc;
    }));

    这就是一种umd写法，既支持Amd 又支持CommonJS，还支持 global


>* ## createStore(reducer,[preloadedState],[enhancer])
* reducer 纯函数，接受 state、action 2个参数 ，返回 一个新的state
* preloadedState state的初始值，可以把服务端传过来的state传递给它，也可以从之前保存的一个会话中恢复一个传给它
如果是 使用combineReducers创建reducer的，它必须是一个对象并与传入的keys值保持一致（对于state 解构的要求）
* enhancer 是一个组合store creator的高阶函数，返回一个新的强化过的create store

>需要使用多个增强器的时候就会选择compose
[小提示] store创建之后，redux 会自动dispatch一个action(这个action我们不需要处理)来用初始的state填充store，如果state为undifined则会返回初始值
对于服务端运行的同构应用，应该为每个请求创建一个store实例，以此让store相隔离（优势目前我也不知道，没有涉及服务端渲染）

>* ## store 官方的定义 只是一个有几个方法的对象并部署以类的范畴，要创建它我们只要把根部的reducer函数传递给createStore就可以了
* getState 返回当前的state树，它与最后一个reducer返回的state相同
* dispatch(action) 分发action，这是触发state变化的唯一途径，使用当前state和传入的action同步调用store对应的reducer函数，同时变化监听器会触发
* 在redux里面只有根reducer返回新state结束之后才会调用事件监听器，再次触发的dispatch可以写在监听回调里面
* action不使用Symbol作为唯一标识的原因是Symbol不是字符串，不可被序列化

* 如果使用applyMiddleware来套住createStore的时候，middleware可以修改action的执行，

* subscribe添加一个变化监听器，由于dispatch执行结束之后就会调用subscribe监听器，肯能会进入不断dispatch的无线循环之中

* replaceReducer（nextReducer） 替换当前用来计算state的reducer，感觉应用场景有点脱离实际

>## combineReducers 的出现意义就是随着应用场景越来越复杂,需要将reducer函数进行拆分，各自相对独立地管理一部分state

    rootReducer = combineReducers({potato:potatoReducer,tomato:tomatoReducer})
    rootState = {
        potato:{
            ...potatoState 对象
        },
        tomato:{
            ...tomatoState 对象
        }
    }

    每个combineReducer传入的reducer都必须满足以下规则：
        所有未匹配到的action，必须把他接收到的第一个参数也就是那个state原封不动返回
        永远不能返回undifined，这个combineReducers 会抛出异常
        如果传入state为undifined则必须返回初始的state，根据这一条规则一般禁止 state为 undifined，而combineReducers会帮你检测你的reducer是否符合标准应该就是第一次的state的初始化


        applyMiddleware     可以让你包装store的dispatch方法来达到你想要的目的

        这里面涉及到一个 Immutable类的实现
>## Redux-thunk 的源码 （14 行代码）
    function createThunkMiddleware(extraArgument) {
        return ({ dispatch, getState }) => next => action => {
            if (typeof action === 'function') {
                return action(dispatch, getState, extraArgument);
            }

            return next(action);
        };
    }

    const thunk = createThunkMiddleware();
    thunk.withExtraArgument = createThunkMiddleware;

    export default thunk;
    每个中间件都是 以store 的 dispatch 和 getState 为命名参数，并返回一个方法

    
>redux 是一个概念性的东西，实际API的源码行数也就那么几行，但想到这种管理state来实行 时间旅行的思维却是跨时代的

