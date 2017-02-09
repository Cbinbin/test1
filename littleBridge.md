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

}
```
## 客户( Customer )
```js
{
	openid: String,		//微信Id
	nickname: String,		//昵称
	sex: String,		//性别
	headimg: String,		//头像
	telephone: Number,		//联系电话

}
```
## 开发人员( Developer )
```js
{
	openid: String,		//微信Id
	nickname: String,		//昵称
	sex: String,		//性别
	headimg: String,		//头像
	
}
```
## 项目( Project )
```js
{
	title: String,		//项目名
	version: String,		//项目版本
	cycle: Number,
	picture: String,
	schedule: String,
}
```