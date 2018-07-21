browser object model

	window
		|
		| -> docuemnt  location  history screen navigator frames 
				|
				| -> anchors[] applets[] areas[] embeds[] forms[] images[] layers[] links[]

location{
	hash
	host
	hostname
	href
	origin
	path
	replace
	reload
}

history{
	back
	forward
	go
	pushState(state,title,url)
	replaceState
	length
	state
}
popstate 事件，是通过浏览器 的前进后退建触发

navigator{
	appCodeName
	appName
-	appVersion
	bluetooth
	budget
	connection
	cookieEnable
	doNotTrack
	geolocation
	hardwareConcurrency
	languages
	maxTouchPoints
	mediaCapabilities
	mimeTypes
	onLine
	permissions
-	platform
	plugins
	presentation
	product
	productSub
	serviceWorker
-	userAgent
	vendor
	vendorSub
}
判断手机型号大多是 通过 正则的形式 与userAgent 进行匹配

screen{
	availHeight
	availWidth
	availTop
	availLeft
	colorDepth
	pixelDepth
	width
}

dpr的理解，H5端 1px的修复 大部分是通过 [dpr]的形式设置，一般的处理是把 viewport的initial-scalbel 为 1，在HTML中设置 dpr


window
	open	打开窗口

	getComponentStyle 可以获取到 元素css中设置的属性值
	IE下则是 currentStyle




	setInterval | clearInterval 一开始用这个进行循环调用
	setTimeout  | clearTimeout

		涉及到 js的 事件循环模型 Loop
			setTimeout	每次执行都会创建一个新的定时器，保证了下一个定时器执行时保证了制定间隔
			而setInterval 只创建一个定时器，让事件执行存在了丢帧的可能，一般发生在程序执行时间大于间隔时间的时候

element的属性
	offset系列  [用于获取距离父级元素以及自身宽高,]
		offsetHeight|offsetWidth  content+padding+border 且数值不带单位
		offsetTop | offsetLeft
		offsetParent 返回最近的具有position:realtive 的父级元素，如果没有则是body
	
	scroll系列 面向 overflow:auto 以及window
		scrollHeight | scrollWidth 不包括 border
		scrollTop | scrollLeft 被卷去的顶部和左边 的距离
		onscroll 滚动触发事件
	
	client系列
		clientX，clientY 获取鼠标在可视区域的位置
		clientWidth，clientHeight content + padding


event
	target 触发事件元素
	currentTarget 当前正在执行事件的元素

	阻止冒泡在IE8之前
		event.cancleBubble = true -> 之后 event.stopPropagation()
		evetn.returnValue = false ->      event.preventDefault()


	其实搭UI 不是最难的，最难的感觉就是 如何将数据有序的可视化，并且在可视化之后这套业务逻辑代码是分离并且可维护的

	开发其实已经从 前后端分离 -> UI业务的分离

	所以对于 redux 需要有一定的深入理解，并且 fetch的封装要与业务逻辑相结合


Dom操作
	查找元素
		getElementById()
		getElementsByName()
		getElementsByTagName()
	[new]
		getElementsByClassName()
		querySelector 返回匹配的第一个元素
		querySelectorAll 返回所有匹配

		firstChild
		lastChild
		childNodes 				存在文本节点，所以一般使用children 获取子元素
		previousSibling
		nextSibling
		parentNode

		createElement()
		createAttribute() 	一般 setAttribute（x,x） 就可以了啊，何来get之说,因为有的属性标签本身不自带的情况下需要自己diy
		createTextNode() 	
		createComment()  创建注释节点	

		appendChild
		insertBefore

		replaceChild
		cloneNode(true) false 仅复制当前节点，true 连子节点一起复制

		removeChild

		getAttribute
		setAttribute
		removeAttribute
