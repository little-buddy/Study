react-native-svg
	Svg
	Circle
	Ellipse
	G
	Text
	TSpan
	TextPath
	Path
	Polygon
	Polyline
	Line
	Rect
	Use
	Image
	Symbol
	Defs
	LinearGradient
	RadialGradient
	Stop
	ClipPath

依赖 d3-shape
-----------------------
react-native-svg-charts
	LineChart
	PieChart
	AreaChart
	StackedAreaChart
	StackedBarChart
	BarChart
	XAxis
	YAxis
	ProgresCircle
	Decorators
	Gird
	Path

	Children

[axis] 轴线
[curve] 曲线

	common Props

data 				渲染的数据结构
yAccessor 			({item})=>item
xAccessor
----------------
xAccessor yAccessor 其实是一个坐标对Point ，data instanceof Array 的时候，下标映射 X，值映射 Y

yScale				[d3Scale.scaleLinear、d3Scale.scaleTime,d3Scale.scaleBand
xScale
svg 				passed react-native-svg component props
animate 			[boolean]
animationDuration	[number]
style 				ViewStyle 属性
curve 				d3.curveLinear
contentInset 		{top,bottom,left,right} inside Of the SVG canvas
numberOfTicks 		默认10 密度吗？
showGrid 			[boolean] 是否显示网线
yMin
yMax
xMax
xMin
children 			react-native-svg components

x
y
width
height
data
ticks

data 只是几个点，然后不同的component用不同的方式把他们连起来

curve 
		/*
		  d3Shape{
		    curveBasic            比 Natural更平滑
		    curveBasisOpen        两端开放
		    curveBasisClosed      首尾闭合
		    curveNatural

		    竖状图
		    curveStep             2端一半开始
		    curveStepAfter        不显示最后一个
		    curveStepBefore       不显示第一个
		    
		    折线图
		    curveLinear
		    curveLinearClosed     闭合
		  }
		*/

Stacked - prefix 前缀，表示多组不同意义的值组成的图表
	一般 data的属性值会与keys对应

[都是必填项]

	data
	keys
	colors


对于 BarChart spacingInner spacingOuter 可以控制每个值之间的间隙

svg{
	fill
	stroke
	onPress
	key
}

XAxis
YAxis
	能够 画出图表的 坐标轴
	formatLabel={(value,index)={}} 用来显示label




