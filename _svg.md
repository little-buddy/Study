
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











 