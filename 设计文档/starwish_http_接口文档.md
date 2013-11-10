###STARWISH HTTP 接口文档

	1.加密
		所有的接口采用salt加密方式来进行调用
		有两种接口：
			1）一种是采用固定salt加密
			2）另一种是采用服务器返回的固定盐加密
		详细如下：
		固定salt（客户端保存）：
			例如：salt ＝ 123456；
			要传入的参数：name＝wiper , age=12
			加密方式：
			salt = md5(name=wiper&age=12&123456)
			调用：
			例如得出的salt为：aaaaddfg23
			调用时要附加上salt = aaaaddfg23
			
		2
					"result":true				
				}

	2.分页
		分页参数：有分页的接口，只需要传page＝n就好。
		如有分页数据会带有这些信息：
		{
			"data":
			"elapse":0,
			"errorCode":0,
			"message":"",
			"result":true			"paging": {				total:1,				size:20,				page:1			}		}
	3.访问链接
		http://域名/
		


## 注册

### 提交账号信息(手机注册)
    url： /api/register/phone/step1
    method : post
    加密方式：固定salt
##### 接口描述
    用户注册第一步，提交账号信息

##### 输入参数：
field|desc
-----|----
account|手机号 


##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）｝

    data数据格式为：
    ｛
        type:"Cellphone",/*用户注册方式 */
        success:true|false,/*激活信息是否发送成功*/
        time:234234/* 下次发送激活信息时间 */
    ｝
       
### 重新发送激活信息
    url： /api/register/send-again
    method: post
	加密方式：固定salt
##### 接口描述
    用户注册时用于重新发布激活信息
    
##### 输入参数： 
field|desc
-----|----
account|手机号
##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）｝

    data数据格式为：
    ｛
        type:"Cellphone",/*用户注册方式 */
        success:true|false,/*激活信息是否发送成功*/
        time:234234/* 下次发送激活信息时间 */
    ｝

### 验证激活码
    url： /api/register/active
    method: post
	加密方式：固定salt
##### 接口描述
		验证手机激活码    
    
##### 输入参数：
field|desc
-----|----
account|账号（手机号）
token|激活码

##### 输出：
field|desc
-----|----
result|ture/false, true表示验证成功,false表示失败
code|状态码
message|提示信息
data|{}

	data数据格式为：
    ｛
        type:"Cellphone",/*用户注册方式 */
        success:true|false,/*注册是否成功*/
        salt:"slkj23423lk4j2oi34"/*登录后的salt*/
        id:"12345678"
    ｝

### 提交用户个人信息
    url： /api/register/step2
    method : post
##### 接口描述
    用户注册第二步，提交用户个人信息
    
##### 输入参数： 
field|desc
-----|----
nickname|昵称
age|年龄
description|个性签名
gender|性别 （值为1/2,1为女，2为男）
areaCode|城市编码
email|邮箱 （如果用户是手机注册那么这项需要填写）
avatar| 头像

##### 输出：
field|desc
-----|----
result|true/false
code|
message|
data|{}


### 提交账号信息(第三方注册)
    url： /api/register/sns/step1
    method : post
    加密方式：固定salt
##### 接口描述
    用户注册第一步，提交第三方账号信息

##### 输入参数：
field|desc
-----|----
token|token
expireTime|过期时间
type|(1/2/3 weibo/qzone/renren)


##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）｝

    data数据格式为：
    ｛
        type:"weibo/renren/qzone",/*用户注册方式 */
        salt:"slkj23423lk4j2oi34"/*登录后的salt*/
        id:"12345678"
    ｝




###上传通讯录
	url： /api/upload/contact
	method : post
##### 接口描述
    上传通讯录，匹配手机好友
    ##### 输入参数：
field|desc
-----|----
contact|通讯录(号码1:号码2:号码3.....)

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|{}（当result为true时，该字段有效)


## 登录

### 手机登录
    url： /api/login/phone
    method : post
    加密方式：固定salt
##### 接口描述
    用户注册第一步，提交账号信息

##### 输入参数：
field|desc
-----|----
account|手机号 


##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）｝

    data数据格式为：
    ｛
        type:"Cellphone",/*用户登录方式 */
        success:true|false,/*激活信息是否发送成功*/
        time:234234/* 下次发送激活信息时间 */
    ｝
       
### 重新发送登录激活信息
    url： /api/login/send-again
    method: post
	加密方式：固定salt
##### 接口描述
    用户注册时用于重新发布激活信息
    
##### 输入参数： 
field|desc
-----|----
account|手机号 
##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）｝

    data数据格式为：
    ｛
        type:"Cellphone",/*用户注册方式 */
        success:true|false,/*激活信息是否发送成功*/
        time:234234/* 下次发送激活信息时间 */
    ｝

### 验证激活码
    url： /api/login/active
    method: post
	加密方式：固定salt
##### 接口描述
		验证手机激活码    
    
##### 输入参数：
field|desc
-----|----
account|账号（手机号）
token|激活码

##### 输出：
field|desc
-----|----
result|ture/false, true表示验证成功,false表示失败
code|状态码
message|提示信息
data|{}

	data数据格式为：
    ｛
        type:"Cellphone",/*用户注册方式 */
        success:true|false,/*注册是否成功*/
        salt:"slkj23423lk4j2oi34"/*登录后的salt*/
    ｝
### sns登录
    url： /api/login/sns
    method : post
    加密方式：固定salt
##### 接口描述
    用户注册第一步，提交第三方账号信息

##### 输入参数：
field|desc
-----|----
token|token
type|(1/2/3 weibo/qzone/renren)

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）｝

    data数据格式为：
    ｛
        type:"weibo/renren/qzone",/*用户注册方式 */
        salt:"slkj23423lk4j2oi34"/*登录后的salt*/
    ｝
##用户信息

### 获取自己个人信息
	url： /api/user/get
	method : get
##### 接口描述
	获取用户得个人信息
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）｝

    data数据格式为：
    ｛
       略
    ｝
### 获取其他用户得信息
	url： /api/user/get
	method : get
##### 接口描述
	获取用户得个人信息
##### 输入参数：	
field|desc
-----|----
userId|用户id
friendId|朋友id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）｝

    data数据格式为：
    ｛
       略
    ｝
### 获取其他用户得信息
	url： /api/user/get
	method : get
##### 接口描述
	获取用户得个人信息
##### 输入参数：	
field|desc
-----|----
userId|用户id
friendId|朋友id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）｝

    data数据格式为：
    ｛
       略
    ｝
    
###修改用户信息
	url： /api/user/modify
	method : get
##### 接口描述
	获取用户得个人信息
##### 输入参数：	
field|desc
-----|----
userId|用户idnickname|昵称
age|年龄
birthday|生日
area|区域
description|描述
imei|imei
os|系统
gender｜性别
avatarz|头像
##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###修改好友得备注名
	url： /api/user/modify/friend
	method : get
##### 接口描述
	修改好友得备注
##### 输入参数：	
field|desc
-----|----
userId|用户id
friendId|朋友id
rname|备注名
##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###获取我的收藏
	url： /api/user/list/favorite
	method : get
##### 接口描述
	获取我的收藏
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###获取我的团（创建的和参加的）
	url： /api/user/list/groups
	method : get
##### 接口描述
	获取我的团
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###获取我的好友列表
	url： /api/user/list/friends
	method : get
##### 接口描述
	获取我的好友列表
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###获取我的陌生人列表
	url： /api/user/list/stranger
	method : get
##### 接口描述
	获取我的陌生人列表
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###获取我的关注明星
	url： /api/user/list/star
	method : get
##### 接口描述
	获取我的关注明星
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）


###获取我的相册
	url： /api/user/list/gallery
	method : get
##### 接口描述
	获取我的关注明星
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###添加我的相册
	url： /api/user/add/gallery
	method : get
##### 接口描述
	添加我的相册
##### 输入参数：	
field|desc
-----|----
userId|用户id
url|链接
type|类型

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）
###删除我的相册
	url： /api/user/add/gallery
	method : get
##### 接口描述
	添加我的相册
##### 输入参数：	
field|desc
-----|----
userId|用户id
sid|资源id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###删除好友
	url： /api/user/delete/friend
	method : get
##### 接口描述
	获取我的关注明星
##### 输入参数：	
field|desc
-----|----
userId|用户id
friendId|朋友id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###添加好友
	url： /api/user/add/friend
	method : get
##### 接口描述
	获取我的关注明星
##### 输入参数：	
field|desc
-----|----
userId|用户id
friendId|朋友id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###确认添加好友
	url： /api/user/add/confirm
	method : get
##### 接口描述
	获取我的关注明星
##### 输入参数：	
field|desc
-----|----
userId|用户id
friendId|朋友id
reply|回执

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###加入黑名单
	url： /api/user/add/blacklist
	method : get
##### 接口描述
	加入黑名单
##### 输入参数：	
field|desc
-----|----
userId|用户id
friendId|朋友id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

##明星

	基本功能的接口和用户的一样，但是会多一些明星的特有功能
###获取明星的音乐
	url： /api/star/list/music
	method : get
##### 接口描述
	获取明星的音乐
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###获取明星额外的信息
	url： /api/star/information
	method : get
##### 接口描述
	获取明星额外的信息
		（我的总收入，我的每天新增收入，
		  我的总粉丝，我的每天的新增粉丝，
		   我的总的团，我每天新增的团）
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###获取明星的聊天内容
	url： /api/star/record
	method : get
##### 接口描述
	获取明星的群聊内容
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###获取明星的产品
	url： /api/star/list/product
	method : get
##### 接口描述
	获取明星的产品
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

##粉丝团

###创建粉丝团
	url： /api/group/add
	method : post
##### 接口描述
	创建粉丝团
##### 输入参数：	
field|desc
-----|----
userId|用户id
starName|所属明星
avatar|头像

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###邀请用户
	url： /api/group/invite
	method : post
##### 接口描述
	邀请用户
##### 输入参数：	
field|desc
-----|----
userId|用户id
groupId|群id
friends|(用户id1:用户id2)

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###修改群资料
	url： /api/group/modify
	method : get
##### 接口描述
	修改群资料
##### 输入参数：	
field|desc
-----|----
userId|用户id
groupId|群id
avatar｜头像
description｜描述
annouce｜公告

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###申请认证
	url： /api/group/verify
	method : get
##### 接口描述
	修改群资料
##### 输入参数：	
field|desc
-----|----
userId|用户id
groupId|群id
description｜描述

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）


###申请认证
	url： /api/group/verify
	method : post
##### 接口描述
	申请认证
##### 输入参数：	
field|desc
-----|----
userId|用户id
groupId|群id
description｜描述

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###修改团员备注
	url： /api/group/modify/member-note
	method : post
##### 接口描述
	修改团员备注
##### 输入参数：	
field|described
-----|----
userId|用户id
groupId|群id
memberId|成员id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###粉丝团踢人
	url： /api/group/delete/member
	method : post
##### 接口描述
	修改团员备注
##### 输入参数：	
field|described
-----|----
userId|用户id
groupId|群id
memberId|成员id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）


###粉丝团解散
	url： /api/group/delete－group
	method : post
##### 接口描述
	修改团员备注
##### 输入参数：	
field|described
-----|----
userId|用户id
groupId|群id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

##商品

	获取用户订单和明星获取自己的产品，在上面已有定义。

###获取单个商品详细信息
	url： /api/product/get
	method : post
##### 接口描述
	获取单个商品详细信息
##### 输入参数：	
field|described
-----|----
productId|商品id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###获取所有商品
	url： /api/product/list
	method : post
##### 接口描述
	获取单个商品详细信息
##### 输入参数：	

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###购买商品
	url： /api/user/add／order
	method : post
##### 接口描述
	购买商品
##### 输入参数：	
field|described
-----|----
productId|商品id
userId｜用户id
phone|电话
postcode|邮编
area|区域
description|描述
address|地址
count|购买数量
description｜购买描述
name|真实姓名

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）

###获取我的订单（已完成购买的和没有完成购买的）
	url： /api/user/list/order
	method : get
##### 接口描述
	获取我的关注明星
##### 输入参数：	
field|desc
-----|----
userId|用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）


###删除购买订单
	url： /api/user/order/delete
	method : post
##### 接口描述
	删除购买商品
##### 输入参数：	
field|described
-----|----
productId|商品id
userId｜用户id

##### 输出：
field|desc
-----|----
result|true/false
code|状态码（当result为false时，该字段有效）
message|（当result为false时，该字段有效）
data|（当result为true时，该字段有效）