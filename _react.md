
React 顶层API

React.Component
React.PureComponent
	PureComponent 比 Component 在shouldComponentUpdate 多了一层浅比较
	它能够跳过整个组件子树的props更新，所以确保所有的子组件也是pure

React.createElement( type , [props] , [...children] )
	等效 ：<element.type {...element.props} {...props}>{children}</element.type>
React.cloneElement( element , [props] ,[...children] )

React.createFactory 


React.isValidElement 
	验证一个元素是否是React元素 boolean

React.Children{
	map
	forEach
	count
	only
	toArray

}

V 16.2.0 版本开始支持，无需额外创建DOM 
React.Fragment
	简写<></>



代码 要将 工作 和 兴趣 分开。只写一堆垃圾业务代码，有空去研究一个框架
这应该是我自身的职业规划，合适且工资高不论干什么就干，也不要管代码质量
那个质量会由上面的人去review一手抓

它应该是用了一堆的正则，然后进行处理

它这里的Modal是一直存在的。通过modal 的 visible 形式设置
我的思路会是通过外层的 state 来控制是否显示
它这里从底层传递了数据给父层，那我们也可以dispatch的形式的，将一些参数通过action传递啊

React 的框架形式就是这样的
v16.3.0 又自身提供了一套context的传递方式，这样可能就会抛弃 react-redux 

但是react-redux 是有一套 更新state机制的