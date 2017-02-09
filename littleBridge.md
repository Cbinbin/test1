### 小桥后台管理： 用户管理、客户管理、开发人员管理、项目管理

## 数据模型
主要的数据模型有这些：admin, user, customer, developer, project    
## 管理员( Admin )
```js
{
	admin: String,		//管理员名
	password: String		//密码
}
```
## 用户( User )
```js
{
	openid: String,		//微信Id
	nickname: String,		//昵称
	sex: String,		//性别
	headimg: String,		//头像
	origin: String		//籍贯
}
```
## 客户( Customer )
```js
{
	openid: String,		//微信Id
	nickname: String,		//昵称
	realname: String,		//真实姓名
	sex: String,		//性别
	headimg: String,		//头像
	origin: String,		//籍贯
	telephone: Number,		//联系电话
	company: String,		//公司名称
	companyLogo: String,		//公司logo
	companyAddress: String,		//公司地址
	fax: String,		//公司传真
	seniority: Number,		//服务年限
	serviceDate: Date,		//服务起始日期
	onGoing: [ ObjectId ],		//正在进行的项目( Project )
	allProjects: [ ObjectId ],		//所有项目( Project )
	remark: String		//备注信息
}
```
## 开发人员( Developer )
```js
{
	openid: String,		//微信Id
	nickname: String,		//昵称
	sex: String,		//性别
	headimg: String,		//头像
	origin: String,		//籍贯
	position: String,		//职位
	phone: Number,		//电话
	QQ: Number,		//QQ
	signature: String,		//个性签名
	introduction: String,		//自我介绍
	status: ['on', 'off'],		//在线状态
	projectTime: Number,		//项目在线时长(单位:分钟)
	totalTime: Number,		//在线总时长(单位:分钟)
	doing: ObjectId,			//正在进行项目( Project )
	participations: [ ObjectId ]		//参与的项目( Project )
}
```
## 项目( Project )
```js
{
	title: String,		//项目名
	version: String,		//项目版本
	picture: String,		//项目图片
	degree: ['pending'(待处理), 'start'(确认需求), 'going'(开发测试), 'check'(验收), 'finish'(完结)],		//项目进度
	schedule: ObjectId,		//项目进度模型
	cycle: Number,		//项目周期
	startDate: Date,		//开始日期
	endDate: Date,			//截止日期
	designs: [ ObjectId ],		//设计图(Design)
	documents: [ ObjectId ],		//开发文档(Document)
	possessor: ObjectId,		//客户
	developers: {		//开发人员
		frontEnd: [ ObjectId ],
		backstage: [ ObjectId ],
		backEnd: [ ObjectId ]
	}
}
```
其他数据模型:    
### 进度(Schedule)
```js
{
	projectId: Object,		//项目Id
	pending: {			//待处理
		time: String,		//时间
		text: String		//文本
	},
	start: {			//需求阶段
		time: String,
		text: String,
		tasks: {
			txt1: String,
			txt2: String,
			txt3: String,
			txt4: String,
			txt5: String,
		}
	},
	going: {			//开发阶段
		time: String,
		text: String,
		taskbar: {
			frontEnd: ObjectId,		//前端界面
			backstage: ObjectId,		//后台界面
			backEnd: ObjectId		//后端开发
		}
	},
	check: {			//反馈阶段
		time: String,
		text: String
	},
	finish: {			//已完结
		time: String,
		text: String
	}
}
```
### 前端界面(FrontEnd)
```js
{
	task1: {
		txt: String,
		completion: Boolean
	},
	task2: {...},
	task3: {...},
	task4: {...},
	task5: {...},
	task6: {...},
	task7: {...},
	task8: {...}
}
```
### 后台界面(Backstage)
```js
{
	task1: {
		txt: String,
		completion: Boolean
	},
	task2: {...},
	task3: {...},
	task4: {...},
	task5: {...},
	task6: {...},
	task7: {...},
	task8: {...}
}
```
### 后端开发(BackEnd)
```js
{
	task1: {
		txt: String,
		completion: Boolean
	},
	task2: {...},
	task3: {...},
	task4: {...},
	task5: {...},
	task6: {...},
	task7: {...},
	task8: {...}
}
```
### UI设计图(Design)
```js
{

	designUrl: String
}
```
### 开发文档(Document)
```js
{
	writer: String
}
```
### 头像(Headimg)
```js
{
	headimgUrl: String
}
```
### 项目图片(Picture)
```js
{
	picUrl: String
}
```