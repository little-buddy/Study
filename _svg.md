
初入 SVG
	svg简单的知识点知道一下就好了，真的制作还是交个 交互人员吧，不能成为我的研究课题

我的研究课题在于如何高效处理缓存，如何搭建一个较好的APP，这是需要丰富的实战经验的

所以搭建一个K线图还是可以的，但是这个需要svg工地


总结下如何去画K线图吧
	
	一般的频率  1分 5分 15分 30分

	 开盘价 收盘价 最高价 最低价

对于这个K线图的一次性展示个数确定，从当天当时的频率算起，数据是服务端实时推送的

缩放的时候以第一个触及的点



对于首页的的数据填充需要的是
* [activities] 中不包含 sleep *
 v1/data/tracking/activities 应该是当天每分钟的活动记录情况

	日 周 月
		cal
		sleep
		distance
		rate
		duration
		steps

心率分 		max min avg，是显示哪种心率呢
活动时间 		beginTime endTime 求差值吗

用于详情页绘制当天图表情况
 v1/data/tracking/activities/hourly/{activity}/{date}

 v1/data/sleep/ 能够获取当天的睡眠持续时间

 6个activity嘛


 /v1/data/challenges/goals/{date} 获取目标记录

 我要再看一下mock的编写 fetch的处理 redux-act的写法 以及 react-navigation处理

 它是没有验证token的有效期的，内设2分钟，实际是无期限的










 var moment = window['moment-range'].extendMoment(moment);
 var start = new Date()
 start.setDate(1)
 var end = new Date()
 console.log(moment.range(start,end))


 2018-02-01

https://prod-api.mykronoz.com

xjqzr2@qq.com


我的理解就是 按天 取hourly 按周 取daily 按月 还是 deily 【 对于图表的api获取 】

activity sleep rate 之间是有区别的


mykronoz 问题总结
	[1]api 中存在 minute 和 hourly ，一天按分划分的数据 一天按小时划分的数据，实际UI 细化到小时，那 heartrate 和 activity 是不是有区别

	[2]homepage的日期是否需要与对应的页面的日期一致，目前我将它分了开来

	[3]切换 day week month的时候，切换回来是需要选择的

	[4]sleep的表盘与数据 对应存在问题啊


	


	fetch('https://api.mykronoz.com/v1/data/personal/avatar',{
		method:'PSOT'
		headers:{
			'Content-Type':'multipart/form-data'
			 'Authorization':'Bearer eyJhbGciOiJIUzI1NiJ9.eyJqdGkiOiJsYktkaFZpWlhKRGVxaG9wN2FuRTNnIiwiaXNzIjoiTXlLcm9ub3ogQWNjb3VudHMgSldUIElzc3VlciAwLjEiLCJzdWIiOiIyZTU2M2U1MDA5N2UzYTJiIiwicm9sZSI6InVzZXIiLCJuYW1lIjoiV0FIQUhBIHQiLCJleHAiOjE1MzA1MTA3MTMsImNvbnRleHQiOnsiZW1haWxfdmFsaWRhdGVkIjpmYWxzZSwicmVnaXN0cmF0aW9uX2RhdGUiOjE1MzAxOTY4ODIwMDAsInR6IjoiVVRDIiwiYWN0aXZlIjp0cnVlLCJsYXN0X25hbWUiOiJ0IiwibG9jYWxlIjoiZW4tVVMiLCJhcHBfaWQiOiI0MmU3MzI0ZjI5YTY0MjM2IiwiZmlyc3RfbmFtZSI6IldBSEFIQSIsImVtYWlsIjoidW5pdmVyc2FsQHRlc3QuY29tIn0sIm5iZiI6MTUzMDI1MTM5MywiYXBwX2lkIjoiNDJlNzMyNGYyOWE2NDIzNiJ9.BH35bXeS5rPGwPpvkHoxscYQ-QAe5_xqYgaPuKXZQoc'，
			 cors:''
		}
		}).then(x=>{console.log(x)})

	但是这里有一个问题，post 已经提交
	取消success的执行，在后续的过程中还是会响应这个success的啊

	不能写在 componentDidUpdate 里面会循环更新

	componentShouldUpdate
	componentWillReceiveProps



	home 是否需要调整 周 月

	我在想一个问题，react-navigation 的参数会收到 this.state的更新影响嘛？


	ZeRound的逻辑：
		首页 与 单项 不关联
		单项返回首页始终显示当天的，首页只显示天，不显示周月



homePage的逻辑
	每次选择 周、月、日的类型变动都会发生请求，然后他们的变动也会

	

	当天的时候能生成，当天 当周 当月
	但是当周 无法生成当天
	当月  无法生成当周 当天

	假如当月进来，那么 周 应该默认当天的周，月应该默认当月的周

	我觉得应该就只有一份数据，当数据类型变了，它自动将那份数据更新到 state中


这周的计划大概就是
	运动列表展示

	骨架屏的设计

	fetch请求中断

	图表类功能的完善

	睡眠时间完善处理

	接上谷歌地图

	这里有个问题我，并不知道手机传给我的数据格式是什么样的啊 延后

	它应该只支持字符数组，而不是 [[][][][][]]这种格式啊


	我不知道它原来的运动列表怎么处理

	对于 sportS 来说	它一定是请求数据到第一次登陆的那天为止
		那中途存在某天没有产生运动Item呢？
		还需要人为进行分页，是否有必要把每个列表都一直展开呢？

		归结起来就是，总长度我不确定，每天的list也不确定，然后快速滑动以及切换的渲染存在问题。这是一个list

		天气获取

		其余最大值。这个问题，

		除了 天气 和 列表 其余都是和 蓝牙交互。不管
		剩下就是 图表的卡顿，地图GPS点的绘制、分享的弹窗








 