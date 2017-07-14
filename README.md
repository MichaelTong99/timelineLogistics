**timelineLogistics** 是模仿淘宝物流信息时间轴界面的自定义View

## 效果

![Markdown](http://i4.piimg.com/1949/af2a87e889d29664.png)

> 使用正则表达式判断字符是否为电话号码，用YYLable进行分文本电话拨打

## 使用
 - 引入Masonry,YYkit库
 	- 使用了MAsonry进行布局
 	- 使用了YYkit中的YYLable进行富文本电话号码点击拨打电话 
 - 初始化数组
 
 		NSArray *titleArr = [NSArray arrayWithObjects:
                         @"[北京通州区杨庄公司锦园服务部]快件已被27号楼e站代签收",
                         @"[北京通州区杨庄公司]到达目的地网店，快件将很快进行派送" ,
                         @"[北京通州区杨庄公司]进行派件扫描；派送业务员：周志军；联系电话：13522464946",
                         @"[北京分拨中心]在分拨中心进行卸车扫描",
                         @"[浙江杭州分拨中心]在分拨中心进行称重扫描",
                         @"[浙江杭州下城区三里亭公司]进行揽件扫描",nil];
    	NSArray *timeArr = [NSArray arrayWithObjects:
                        @"2017-07-04 12:59:00",
                        @"2017-07-03 10:59:00",
                        @"2017-07-03 08:22:00",
                        @"2017-07-03 03:34:22",
                        @"2017-07-02 12:59:00",
                        @"2017-07-02 08:10:00",nil];
                        
 - 转为模型

 		for (NSInteger i = titleArr.count-1;i>=0 ; i--) {
        OKLogisticModel * model = [[OKLogisticModel alloc]init];
        model.dsc = [titleArr objectAtIndex:i];
        model.date = [timeArr objectAtIndex:i];
        [self.dataArry addObject:model];
    	}
    	
 - 初始化控制器

 		OKLogisticsView * logis = [[OKLogisticsView alloc]initWithDatas:self.dataArry];
    	// 给headView赋值
    	logis.wltype=@"已签收";
    	logis.number = @"3908723967437";
    	logis.company = @"韵达快运";
    	logis.phone = @"400-821-6789";
    	logis.imageUrl = @"http://pic40.nipic.com/20140420/12064170_201114370112_2.jpg";
    	logis.frame = CGRectMake(0, 64, OKScreenWidth, OKScreenHeight-64);
    	[self.view addSubview:logis];

> 如果对你有帮助麻烦点个Star
> 
> 我的博客[Oragekk's Blog](http://oragekk.me)