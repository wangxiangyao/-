# 想星后台API接口文档
  
  
* [想星后台API接口文档](#想星后台api接口文档 )
	* [更新说明](#更新说明 )
	* [文档编写规范说明](#文档编写规范说明 )
		* [基本规则说明](#基本规则说明 )
		* [返回结果](#返回结果 )
		* [接口书写规则](#接口书写规则 )
	* [未完善部分](#未完善部分 )
	* [枚举值说明](#枚举值说明 )
	* [说明](#说明 )
		* [空值说明](#空值说明 )
		* [code说明](#code说明 )
		* [通用错误状态返回说明](#通用错误状态返回说明 )
	* [根路径](#根路径 )
	* [登陆](#登陆 )
		* [账户密码登陆](#账户密码登陆 )
		* [token登陆 （放一放）](#token登陆-放一放 )
	* [用户](#用户 )
		* [批量查询](#批量查询 )
		* [单个查询](#单个查询 )
	* [订单](#订单 )
		* [批量查询](#订单批量查询 )
		* [单个查询](#订单单个查询 )
	* [用户地址](#用户地址 )
		* [批量查询](#用户地址批量查询 )
	* [用户积分](#用户积分 )
		* [批量查询](#用户积分批量查询 )
	* [用户包期卡](#用户包期卡 )
		* [批量查询](#用户包期卡批量查询 )
		* [单个查询](#用户包期卡单个查询 )
	* [商品](#商品 )
		* [批量查询](#商品批量查询 )
		* [单个查询](#商品单个查询 )
	* [系统菜单](#系统菜单 )
		* [根据系统用户id查询用户拥有的菜单](#根据系统用户id查询用户拥有的菜单 )
		
  
## 更新说明
- 2018/4/12 `v1.1.2`
	- 周晨阳
		- 增加枚举值说明
		- 新增订单接口文档说明 
- 2018/4/11 `v1.0.1` 
  - 周晨阳 
    - 添加枚举值说明部分，对现有枚举值进行说明
    - 统一错误/正常通用返回字段：统一使用code message
    - 完善接口返回字段描述
  - 王相尧
    - 完善文档样式
    - 添加导航
  
- 2018/4/9 王相尧 周晨阳 `v1.0.0`
  - 讨论并完成`v1`版本接口文档，包括：
    - 文档书写规则
    - 文档说明：空值说明，token说明，接口定义说明
    - 根路径
    - 接口返回统一格式
    - 接口主体定义
      - 登陆
      - 用户
        - 批量查询
        - 单一查询
  
## 文档编写规范说明
  
### 基本规则说明
  
- 协议基于HTTP（此处待议）
- URL 资源请求路径，主要为名词复数
  - 一般以对象名词命名路径，避免动词出现
- 请求参数共三种：URL参数，query参数，请求体参数
- GET用于获取
- POST用于创建
- PUT用于修改——用户提供完整修改数据
- PATCH 用于修改——用户提供修改的字段
- DELETE用于删除
- 过滤查询
  - 可以通过URL参数
  - 也可通过query参数
  - 过滤查询允许冗余
  
### 返回结果
  
- GET `/models` 返回资源列表
- GET `/models/:target` 返回单个target资源
- POST `/models` 返回新生成的对象
- PUT `/models/:target` 返回完整的target资源
- PATCH `/models/:target` 返回完整的target资源
- DELETE `/models/:target` 返回空文档
  
### 接口书写规则
  
需要说明
  - 请求方法
  - URL
  - 各种参数说明
  - 返回示例
    - 说明字段含义
    - 枚举错误返回状态
  
## 未完善部分
  
  - 权限说明
  
## 枚举值说明

- <span id = "activeFlag(有效类型)">activeFlag(有效类型)</span>
  
|  key      |    Value | 
| :-------- | :--------:| 
|  NO | 无效 |  
|  YES     |   有效 | 

  
- type(用户类型)
  
|  key      |    Value | 
| :-------- | :--------:| 
|  COMMON | 普通会员 |  
|  EXPERIENCE     |   体验卡会员 | 
|  TWO_STAR      |    双星卡会员 | 
|  FOUR_STAR      |    四星卡会员 | 
|  SIX_STAR      |    六星卡会员 | 
  
- <span id = "realNameAuthStatus(实名认证状态)">realNameAuthStatus(实名认证状态)</span>
  
|  key      |    Value | 
| :-------- | :--------:| 
|  NO_AUTH | 未认证 |  
|  IN_AUTH     |   认证中 | 
|  AUTH_SUCCESS      |    认证成功 | 
|  AUTH_FAIL     |   认证失败|

- appType(用户App类型状态)
  
|  key      |    Value | 
| :-------- | :--------:| 
|  H5| H5 |  
|  IOS|   IOS | 
|  ANDROID|  ANDROID   | 
|  WECHAT_MINI_PROGRAM|   WECHAT_MINI_PROGRAM|
  
- <span id="marketingPeriodCardCategoryType(包期卡类别)">marketingPeriodCardCategoryType(包期卡类别)</span>
  
|  key      |    Value | 
| :-------- | :--------:| 
|  EXPERIENCE | 体验卡 |  
|  TWO_STAR     |   双星卡 | 
|  FOUR_STAR      |    双星卡 | 
|  SIX_STAR     |   六星卡|
  
- <span id="origin(包期卡来源)">origin(包期卡来源)</span>
  
|  key      |    Value | 
| :-------- | :--------:| 
|  BUY_BY_USER | 用户在线自购 |  
|  UPGRADE     |   升级 | 
|  TRANSFER_BY_FRIEND      |    好友转赠 | 
|  GIVE_BY_PLATFORM     |   平台赠送|
|  RECEIVE     |   领取|
|  BUY_BY_ENTITY_CARD     |   用户线下实体卡购买|
|  DEPOSIT_TO_PERIOD_CARD     |   押金转年卡|
  
- payChannel(支付渠道)
  
|  key      |    Value | 
| :-------- | :--------:| 
|  ALIPAY | 支付宝 |  
|  WEIXIN     |   微信 | 
  
- bussinessType(用户支付业务类型)
  
|  key      |    Value | 
| :-------- | :--------:| 
|  PERIOD_CARD_NEW_PAY | 包期卡新卡支付 |  
|  PERIOD_CARD_UPGRADE_PAY     |   包期卡升级支付 | 
|  DEPOSIT_RECHARGE     |   押金充值 | 
|  DEPOSIT_ORDER_NEW     |   押金订单新订单 | 
|  DEPOSIT_ORDER_CONTINUE_RENT     |   押金订单续租 | 
|  ORDER_COMPENSATE     |   订单赔付 | 
  
- <span id="status(用户包期卡状态)">status(用户包期卡状态)</span>
  
|  key      |    Value | 
| :-------- | :--------:| 
|  OPENED | 已开通 |  
|  NOT_OPEN     |   未开通 | 
|  IN_TRANSFERING     |   转赠中 | 
|  INVALID_BY_EXPIRE     |   到期已失效 | 
|  INVALID_BY_UPGRADE     |   被升级已失效 | 
|  INVALID_BY_TRANSFER     |   被转赠已失效 | 

-  rentMethod(租赁方式)

|  key      |    Value | 
| :-------- | :--------:| 
|  RENT_BY_PERIOD_CARD | 包期卡租赁 |  
|  RENT_BY_DEPOSIT     |   押金租赁 | 
-  <span id = "status(订单状态)">status(订单状态)</span>

|  key      |    Value | 
| :-------- | :--------:| 
|  NEW_PURCHASE_WAIT_PAY | 新订单待付款 |  
|  PAYED_AND_PREPARING     |   准备中 | 
|  PREPARED_AND_DISPATCHING     |   派送中 | 
|  RECEIVED_AND_SIGNED     |   已签收 | 
|  LEASE_TIMEOUT     |   租期超时 | 
|  RESERVED_FOR_RETURN     |   已预约还货 | 
|  RETURN_ON_THE_WAY     |   返仓中 |
|  WAIT_COMPENSATE     |   待赔付 |
|  RETURNED_AND_SUCCESS     |   交易成功 |
|  CANCELED     |  已取消 |
|  PAY_TIMEOUT     |   超时未支付 |

- 	  evaluateStatus(评价状态)

|  key      |    Value | 
| :-------- | :--------:| 
|  CAN_NOT_EVALUATE     |   不可评价 |
|  WAIT_TO_EVALUATE     |   待评价 |
|  EVALUATED     |   已评价 |

- 	  rentType(订单详情租赁类型)

|  key      |    Value | 
| :-------- | :--------:| 
|  COMMON_RENT|   正常租赁 |
|  CONTINUE_RENT|   续租 |

- 	  type(物流类型)

|  key      |    Value | 
| :-------- | :--------:| 
|  RECEIVE_COMMODITY|   收件 |
|  RETURN_COMMODITY|   还件 |
  
  
  - 	  <span id="operateType(用户积分操作类型)">operateType(用户积分操作类型)</span>

|  key      |    Value |
| :-------- | :--------:| 
|  DEPOSIT_PURCHASE_RETURN|   押金租赁订单完成还货|
|  EXPERIENCE_CARD_BUY|   成功购买体验卡 |
|  TWO_STAR_CARD_BUY|   成功购买双星卡|
|  FOUR_STAR_CARD_BUY|   成功购买四星卡 |
|  SIX_STAR_CARD_BUY|   成功购买六星卡|
|  NEW_USER_REGISTER|   注册 |
|  PURCHASE_RETURN|   订单还货完成|
|  DEPOSIT_PURCHASE_CONTINUE_RENT|   押金租赁订单续租 |
|  DEPOSIT_PURCHASE_CHANGE_RENT|   押金租赁订单换租|
|  INVITED_USER_FIRST_DEPOSIT_PURCHASE_RETURN|   邀请用户首次完成押金租赁订单 |
|  INVITED_USER_FIRST_EXPERIENCE_CARD_BUY|   邀请用户首次购买体验卡|
|  INVITED_USER_FIRST_TWO_STAR_CARD_BUY|   邀请用户首次购买双星卡 |
|  INVITED_USER_FIRST_FOUR_STAR_CARD_BUY|   邀请用户首次购买四星卡|
|  INVITED_USER_FIRST_SIX_STAR_CARD_BUY|   邀请用户首次购买六星卡 |
|  PURCHASE_CANCELED|   订单取消退回|
|  PURCHASE_PAY_TIMEOUT|   订单超时未支付 |
|  DEPOSIT_PURCHASE_RENT_DEDUCT|   押金租赁订单完成还货|
|  DEPOSIT_PURCHASE_CONTINUE_RENT_DEDUCT|   押金租赁订单租金抵扣 |
|  DEPOSIT_PURCHASE_RETURN|   押金租赁订单租金抵扣|
|  CARD_UPGRADE_DEDUCT|   会员卡升级 |
|  INTEGRAL_EXCHANGE_30_DAYS|   积分兑换30天时长 |
  
## 说明
  
  
- 账号由超级管理员统一分配
- 除了登陆请求，所有请求都需要带token，token放在请求头的`Authorization`字段中
- 注意：由于url本身传递String类型，所以，对于`URL参数`，`query参数`，类似id应该是number类型，但是通过url本身传递，会被转换为String
  
### 空值说明
  
- 所有数据字段必须返回：
  - 空值：
    - 字符串，数字： 不返回
    - 数组：[]
    - 对象：{}
  
### code说明
  
|  key      |    Value | 
| :-------- | :--------:| 
| 200		|ok|
| 401| 账号未登录|
| 401| 账号没有权限|
| 500	|	系统异常 |
|1001	|账号或者密码错误|
|1002	|查询参数错误|
|1003	|查询CWMS错误|
  
  
### 通用错误状态返回说明
  
```javascript
{
  code: 1001,
  message: "账号或者密码错误"
}
```
  
## 根路径
  
  
`/api/v1/`
  
## 登陆
  
  
### 账户密码登陆
  
  
- 请求方法：`POST`
- URL `/login`
- 请求体参数：
  
| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| account | String | 是 | 超级管理员分配的账号 | 13213195318 | 
| password | String | 是 | 管理员密码 | aaabbbccc |
  
- 返回示例：
``` javascript
// 正常
{
    code: 200,
    message: "ok",
    data: {
        id: String 用户id,
        token: String 用户唯一标识
    }
}
  
// 错误情况
{
    code: 1001,
    message: "账户或密码错误",
}
```
  
- 说明：
  - token过期时间：30天
  
### token登陆 （放一放）
  
  
- 请求方法：`POST`
- 
  
## 用户
  
  
### 批量查询
  
  
- 请求方法： `GET`
- URL：`/user`
- query参数：
  
| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| page | Number | 是 | 请求页码 | 10 请求第10页 |
| limit | Number | 是 | 每页数据量 | 10 |
| userId | Number | 否 | 用户id | 1 |
| nickName | String | 否 | 用户昵称 | 布雷布雷 |
| sex | Enum-String | 否 | 性别：MALE(男)，FEMALE(女) | MALE |
| mobile| String | 否 | 用户手机 | 13817325685|
| realName| String | 否 | 用户真实姓名| 布雷|
| idCardNo| String | 否 | 用户身份证| 310xxx19990909111X|
| realNameAuthStatus| Enum-String | 否 | 是否实名认证| [详情见枚举说明](#realNameAuthStatus(实名认证状态))|
| registerTime | [DateTime-number, DateTime-number] | 否 | 注册时间区间 [开始，结束] 0表示不限制 | [0, 1523242919345], [1523242919345, 0] |
| periodCardHoldFlag | Enum-String | 否 | 是否持有包期卡 | [详情见枚举说明](#activeFlag(有效类型))|
| type | Enum-String | 否 | 用户类型：COMMON("普通会员"), EXPERIENCE("体验卡会员"), TWO_STAR("双星卡会员"), FOUR_STAR("四星卡会员"), SIX_STAR("六星卡会员") |  |
  
- 返回示例
``` javascript
// 正常
{
  code: 200,
  message: 'ok',
  data: {
    count: Number 总数据量
    list: [
      {
	  	"id": Number 用户id,
		"type": Enum-String 用户类型,
		"typeName": String 用户类型中文,
		"realNameAuthStatus":Enum-String  用户是否实名认证,
		"realNameAuthStatusName": String 用户是否实名认证中文,
		"sex": Enum-String 用户性别枚举,
		"sexName": String 性别中文,
		"nickName": String 昵称,
		"mobile": String 用户手机,
		"headImage": String 用户头像url,
		"appType": Enum-String 用户app类型,
		"shareOriginChannel": String 分享来源渠道,
		"activityChannel": String 活动渠道,
		"wechatOpenId":String 微信openID
		"wechatUnionId": String 微信unionID,
		"wechatMpOpenId": String 微信公众平台openid,
		"wechatOpenOpenId":String 微信开放平台openid
        "wechatAuthDatetime": Date-Number 微信认证时间,
		"wechatAuthDatetimeStr": String 微信认证时间中文,
	    
		"totalDeposit": Number 总押金,
		"usableDeposit":Number 可用押金,
		"freezedDeposit":Number 冻结押金
		"totalQuota": Number 总计额度,
		"usableQuota": Number 可以额度,
		"freezedQuota": Number 冻结额度,
		"totalIntegral": Number 总计积分,
        "historyTotalIntegral": Number 历史总积分,
        "orderProfitIntegral": Number 订单收益积分,
        "communityPraiseIntegral": Number 社区点赞积分,
        "continueRentIntegral": Number 续租积分,
		"shareProfitIntegral": Number 分享收益积分,
		"postCommentIntegral": Number 发帖评论积分,
		"changeRentIntegral": Number 换租积分,
		"brandNewsCollectionNumber": Number 品牌资讯收藏数,
        "invitedUserRegisterNumber": Number 已邀请注册用户,
		"brandCollectionNumber": Number 品牌收藏数,
		"invitedUserBuyPeriodCardNumber": Number 已邀请且购买包期卡用户数,
		"brandNewsCommentNumber": Number 品牌资讯评论数,
		"commidityCollectionNumber": Number 商品收藏数,
		"invitedUserPlacePurchaseNumber": Number 已邀请且下单用户数，
        "periodCardHoldFlag":Enum-String 是否持有包期卡,
		"createDatetime": Date-NUmber 用户创建时间,
        "createDatetimeStr": String 用户创建时间中文,
        "activeFlag": Enum-String 数据有效性,
        "version": Number 版本,

      }
      ...
    ]
  }
}
  
// and so on
```
  
### 单个查询
  
  
- 请求方法：`GET`
- URL：`/user/:id`
- URL参数
  
| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| id | Number | 是 | 用户id | 1 | 
  
- 返回示例：
```javascript
{
  "code": 200,
  "message": "OK",
  "data": {
	  	"id": Number 用户id,
		"type": Enum-String 用户类型,
		"typeName": String 用户类型中文,
		"realNameAuthStatus":Enum-String  用户是否实名认证,
		"realNameAuthStatusName": String 用户是否实名认证中文,
		"sex": Enum-String 用户性别枚举,
		"sexName": String 性别中文,
		"nickName": String 昵称,
		"mobile": String 用户手机,
		"headImage": String 用户头像url,
		"appType": Enum-String 用户app类型,
    "shareOriginChannel": String 分享来源渠道,
    "shareOriginUserId": String 分享人
		"activityChannel": String 活动渠道,
		"wechatOpenId":String 微信openID
		"wechatUnionId": String 微信unionID,
		"wechatMpOpenId": String 微信公众平台openid,
		"wechatOpenOpenId":String 微信开放平台openid
        "wechatAuthDatetime": Date-Number 微信认证时间,
		"wechatAuthDatetimeStr": String 微信认证时间中文,
	    
		"totalDeposit": Number 总押金,
		"usableDeposit":Number 可用押金,
		"freezedDeposit":Number 冻结押金
		"totalQuota": Number 总计额度,
		"usableQuota": Number 可以额度,
		"freezedQuota": Number 冻结额度,
		"totalIntegral": Number 总计积分,
        "historyTotalIntegral": Number 历史总积分,
        "orderProfitIntegral": Number 订单收益积分,
        "communityPraiseIntegral": Number 社区点赞积分,
        "continueRentIntegral": Number 续租积分,
		"shareProfitIntegral": Number 分享收益积分,
		"postCommentIntegral": Number 发帖评论积分,
		"changeRentIntegral": Number 换租积分,
		"brandNewsCollectionNumber": Number 品牌资讯收藏数,
        "invitedUserRegisterNumber": Number 已邀请注册用户,
		"brandCollectionNumber": Number 品牌收藏数,
		"invitedUserBuyPeriodCardNumber": Number 已邀请且购买包期卡用户数,
		"brandNewsCommentNumber": Number 品牌资讯评论数,
		"commidityCollectionNumber": Number 商品收藏数,
		"invitedUserPlacePurchaseNumber": Number 已邀请且下单用户数，
        "periodCardHoldFlag":Enum-String 是否持有包期卡,
		"createDatetime": Date-NUmber 用户创建时间,
        "createDatetimeStr": String 用户创建时间中文,
        "activeFlag": Enum-String 数据有效性,
        "version": Number 版本,

      }
}

  // and so on
```
## 订单
  
  
### 订单批量查询
- 请求方法： `GET`
- URL：`/purchase`
- query参数：

| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| page | Number | 是 | 请求页码 | 10 请求第10页 |
| limit | Number | 是 | 每页数据量 | 10 |
|id|String|否|订单id|147|
|purchaseNo|String|否|订单编号|201803131632450617185|
|createTime|[DateTime-number, DateTime-number]|否|下单时间|[0,15379687546]|
|rentTime|[DateTime-number, DateTime-number]|否|租赁开始结束时间|[0,15379687546]|
|appointmentReceiveTime|[DateTime-number, DateTime-number]|否|预约取货开始结束时间|[0,15379687546]|
|appointmentReturnTime	|[DateTime-number, DateTime-number]|否|预约还货开始结束时间|[0,15379687546]|
|receiveMobile	|String|否|收货人手机|18814723696|
|returnMobile	|String|否|还货人手机|18814723696|
|rentMethod	|Enum-String|否|租赁方式|详情见枚举的说明|
|commodityName	|String|否|商品名称|XXX包|
|commodityNo	|String|否|货号|B0000014|
|userRealName	|String|否|用户真实姓名|畅畅小姐姐|
|status	|Enum-String|否|订单状态|[详情见枚举的说明](#status(订单状态))|

- 返回示例：
```javascript
{
  "code": 200,
  "message": "OK",
  "data": {
    "count": 61,
    "list": [
      {
	  "purchaseNo": String ,订单编号
	  "id": Number,订单id
	  "winIntegral": Number, 获得的积分
	  "usedIntegral": Number 使用积分
	  "rentMethodName": String, 租赁方式中文
	  "rentMethod": Enum-String,租赁方式英文
	  "payDeposit": Number,支付的押金
	  "payRentAmount": Number,支付租金
	  "payTotalAmount":Number 支付总金额
	  "rentPrice":Number  租赁价,
	  "freezedQuota": Number 冻结额度
	  "commodityId": Number 商品id
	  "commodityCwmsCode": String 商品cwmscode,
	  "commodityNo": String 商品编号,
	  "commodityName": String 商品名称
	  "commodityColor": String 商品颜色,
	  "commoditySize": String 商品尺寸
	  "rentCycle": String, 租赁周期中文
	  "rentCycleNumber": Number 租赁周期数,
	  "userId": Number 用户id,
	  "userRealName": String 用户真实姓
	  "evaluateStatusName": String 评价状态中文,
	  "evaluateStatus": Enum-String 评价状态
	  "status": String 订单状态
	  "activeFlag": Enum-String 数据状态
	  "version":Number 版本
	  "rentEndDatetime": DateTime-number 租赁结束时间
	  "rentStartDatetime": DateTime-number,租赁开始时间
	  "rentStartDatetimeStr": String 租赁开始时间中
	  "rentEndDatetimeStr": String 租赁结束时间中文
	  "receiveAreaMostSuperiorCommonAreaNameId": Number 一级取货地址id
	  "receiveAreaMostSuperiorCommonAreaName": String 一级取货地址中文,
	  "receiveAreaParentCommonAreaNameId": Number 二级取货地址id
	  "receiveAreaParentCommonAreaName": String,二级取货地址中文  
	  "receiveAreaCommonAreaNameId": 三级取货地址id,
	  "receiveAreaCommonAreaName": String 取货地址中文
	  "receiveName": String 取货人姓名,
	  "receiveMobile":String 取货人手机号
	  "receiveAreaId": Number 取货地址id
	  "receiveAddress": String 取货地址
	  "appointmentReceiveStartDatetime": DateTime-String取货开始时间
	  "appointmentReceiveEndDatetime": DateTime-number 取货结束时间,
	  "appointmentReceiveStartDatetimeStr": String 取货开始时间
	  "appointmentReceiveEndDatetimeStr": String 取货结束时间
	  "returnAreaMostSuperiorCommonAreaNameId": Number 一级还货地址id
	  "returnAreaMostSuperiorCommonAreaName":String  一级还货地址中文,
	  "returnAreaParentCommonAreaNameId": Number 二级换货地址id
	  "returnAreaParentCommonAreaName": String 二级还货地址中文
	  "returnAreaCommonAreaNameId": Number 三级还货地址id
	  "returnAreaCommonAreaName":String 三级换货地址中文,
	  "returnAreaId": Number,还货地址id
	  "returnAddress": String 还货地址,
	  "returnName":String  还货人姓名
	  "returnMobile": String 还货人手机号
	  "appointmentReturnStartDatetimeStr":String 还货开始时间 
	  "appointmentReturnEndDatetimeStr": String 还货结束时间,
	  "appointmentReturnStartDatetime": DateTime-String 还货开始时间
	  "appointmentReturnEndDatetime": DateTime-String 还货结束时间
	  "createDatetimeStr": String 订单创建时间,
	  "createDatetime": DateTime-String 订单创建时间

      }
    ]
  }
}
```

### 订单单个查询
  
  
- 请求方法：`GET`
- URL：`/purchase/:id`
- URL参数
  
| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| id | Number | 是 | 订单id | 1 | 

- 返回示例：
```javascript
{
  "code": 200,
  "message": "OK",
  "data": {
	"id": Number 订单id,
	"purchaseNo": String 订单编号,
	"statusName": String 订单状态中文,
    "status":Enum-String 订单状态
    "rentTypeName": String 租赁类型中文,
    "rentType": Enum-String 租赁类型,
    "rentCycleNumber": Number 租赁周期数,
	"serialNo": String 序列号(支付用),
    "discountRate": Number 折扣率,
    "winIntegral": Number 赢得的积分,
    "rentMethodName": String 租赁方式中文,
    "rentMethod": Enum-String 租赁方式,
    "rentCycleName": String 租赁周期中文,
    "rentCycle": Enum-String 租赁周期 ,
    "evaluateStatusName": String 评价状态中文,
    "payTotalAmount": Number 支付总金额,
    "discountAmount": Number 抵扣总金额,
    "payDeposit": Number 支付押金金额,
    "rentPrice": Number 租赁价格,
    "originalRentAmount": Number 原始租金,
    "payRentAmount": Number 支付租赁金额,
    "freezedQuota": Number 冻结额度,
    "usedIntegral": Number 使用的积分,
    "integralDeductionAmount": Number 积分抵扣金额,
    "commodityId": Number 商品id,
    "commodityNo": String 商品货号,
    "commodityColor": String 商品颜色,
    "commoditySize": String 商品尺寸,
    "commodityCwmsCode": String 商品cwmscode,
    "commodityName":String 商品名称
    "userId": Number 用户id,
    "userRealName": String 用户真实姓名,
    "evaluateStatus": Enum-String 评价状态枚举,
    "createDatetimeStr": String 订单创建时间中文 ,
    "createDatetime": Date-Number 订单创建时间,
    "rentStartDatetime": Date-Number 租赁开始时间,
    "rentEndDatetime": Date-Number 租赁结束时间,
    "rentStartDatetimeStr": String 租赁开始时间中文,
    "rentEndDatetimeStr": String 租赁结束时间,
    "appointmentReceiveStartDatetimeStr": String 预约收货开始时间中文,
    "appointmentReceiveEndDatetimeStr": String 预约收货结束时间中文,
    "appointmentReceiveStartDatetime": Date-Number 预约收货开始时间,
    "appointmentReceiveEndDatetime": Date-Number 预约收货结束时间,
    "receiveAreaMostSuperiorCommonAreaNameId":Number 一级取货地址id,
    "receiveAreaMostSuperiorCommonAreaName": String 一级取货地址中文,
    "receiveAreaParentCommonAreaNameId": Number 二级取货地址id,
    "receiveAreaParentCommonAreaName": String 二级取货地址中文,
    "receiveAreaCommonAreaNameId": Number 三级取货地址id,
    "receiveAreaCommonAreaName": String 三级取货地址中文,
    "receiveMobile": String 取货人手机,
    "receiveName": String 取货人姓名,
    "receiveAddress": String 取货人地址,
    "receiveAreaId": Number 取货区域id,
    "appointmentReturnStartDatetimeStr": String 预约还货开始时间中文,
    "appointmentReturnEndDatetimeStr": String 预约还货结束时间中文,
    "appointmentReturnStartDatetime": Date-Number 预约还货开始时间,
    "appointmentReturnEndDatetime": Date-Number 预约还货结束时间,
    "returnAreaMostSuperiorCommonAreaNameId": Number 一级还货地址id,
    "returnAreaMostSuperiorCommonAreaName": String 一级还货地址中文,
    "returnAreaParentCommonAreaNameId": Number 二级还货地址id,
    "returnAreaParentCommonAreaName": String 二级还货地址中文,
    "returnAreaCommonAreaNameId": Number 三级还货地址id,
    "returnAreaCommonAreaName": String 三级还货地址中文,
    "returnMobile": String 还货人手机,
    "returnName": String 还货人姓名,
    "returnAddress": String 还货人地址,
    "returnAreaId": Number 还货区域id,
    "activeFlag": Enum-String 数据状态,
    "version": Number 版本id,
    "purchaseLogisticsList": [//订单物流列表
		{
		"id": Number 订单物流id,
        "createDatetime": Date-Number 订单物流创建时间,
        "createDatetimeStr": String 订单物流创建时间中文,
        "purchaseId": Number 订单id,
        "type": Enum-String 物流类型枚举,
        "typeName": String 物流类型,
        "description": String 描述,
        "activeFlag": Enum-String 物流数据状态
        "version": Number 物流数据版本号,
      }
	],
    "purchaseCompensationList": [],//订单赔付(留字段)
    "purchaseOperateList": [//订单操作列表
      {
	    "id": Number 订单操作表id,
        "createDatetime": Date-Number 操作创建时间,
        "createDatetimeStr": String 操作创建时间中文,
        "purchaseId": Number 订单id,
        "operateTypeName": String 操作类型中文,
        "operateType": Enum-String 操作类型枚举,
        "statusName": String 操作时的订单状态,
        "status": Enum-String 操作时订单状态枚举,
        "activeFlag": Enuum-String 订单操作数据状态,
        "version": Number 订单操作版本,
      }
    ],
   
  }
}
```

## 用户地址
  
  
### 用户地址批量查询
- 请求方法： `GET`
- URL：`/userAddress`
- query参数：

| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| page | String | 是 | 请求页码 | 10 请求第10页 |
| limit | String | 是 | 每页数据量 | 10 |
| userId | String | 否 | 用户id | 347 |

- 返回示例：
```javascript
{
  "code": 200,
  "message": "OK",
  "data": {
    "count": 2,
    "list": [
      {
	  	"id": Number 用户地址id,
		"userId": Number 用户id,
        "defaultFlag": 是否默认地址,
        "mostSuperiorCommonAreaNameId":Number 一级地址id ,
		"mostSuperiorCommonAreaName": String 一级地址中文,
		"parentCommonAreaNameId": Number 二级地址id,
		"parentCommonAreaName": String 二级地址中文,
		"commonAreaNameId": Number 三级地址id,
		"commonAreaName": String 三级地址中文,
		"commonAreaId": Number 地址id,
		"address": String 收货人详细地址,
        "mobile": String 收货人手机,
        "name": String 收货人姓名,
		"activeFlag": Enum-String 数据状态,
        "version": Number 版本
      }
    ]
  }
}
```
## 用户积分
  
  
### 用户积分批量查询
- 请求方法： `GET`
- URL：`/userIntegral`
- query参数：

| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| page | String | 是 | 请求页码 | 10 请求第10页 |
| limit | String | 是 | 每页数据量 | 10 |
| userId | String | 否 | 用户id | 347 |

- 返回示例：
```javascript
{
  "code": 200,
  "message": "OK",
  "data": {
    "count": 25,
    "list": [
      {
	    "id": Number 用户积分记录id,
	    "userId": Number 用户id347,
	    "operateIntegral": Number 操作的积分,
	    "totalIntegral": Number 总共的积分,
	    "operateType": Enum-String 操作类型,
        "operateTypeName": String 操作类型中文,
        "activeFlag": "YES",
        "version": 1,
      }
    ]
  }
}
```

## 用户包期卡
  
  
### 用户包期卡批量查询
- 请求方法： `GET`
- URL：`/userPeriodCard`
- query参数：

| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| page | String | 是 | 请求页码 | 10 请求第10页 |
| limit | String | 是 | 每页数据量 | 10 |
| userId | String | 否 | 用户id | 347 |
| userMobile| String | 否 | 用户手机 | 138137XXXXX |
| userRealName| String | 否 | 用户真实姓名 | 周XX |
| userNickName| String | 否 | 用户昵称 | 测试昵称 |
| userSex| Enum-String| 否 | 性别：MALE(男)，FEMALE(女) | MALE |
| origin| Enum-String | 否 | 用户包期卡来源枚举 | [详情见枚举的说明](#origin(包期卡来源)) |
| status| Enum-String| 否 | 包期卡状态枚举 | [详情见枚举的说明](#status(用户包期卡状态))|
| type| Enum-String| 否 | 包期卡类别枚举 | [详情见枚举的说明](#marketingPeriodCardCategoryType(包期卡类别))|
| createDatetime| String | 否 | 购卡时间 | [0,15379687546] |

- 返回示例：
```javascript
	{
  "code": 200,
  "message": "OK",
  "data": {
    "count": 119,
    "list": [
      {
	    "id": Number 包期卡id,
	    "userId": Number 用户id,
	    "userRealName": String 用户真实姓名,
	    "userNickName": String 用户昵称,
	    "userSex": Enum-String 用户性别枚举,
	    "userSexName": String 用户性别中文,
	    "userMobile": String 用户手机号,
	    "idCardNo": String 身份证,
	    "marketingPeriodCardCategoryId": Number 包期卡类别id,
	    "marketingPeriodCardCategoryType": Enum-String 包期卡类别枚举,
	    "marketingPeriodCardCategoryName": String 包期卡类别中文,
        "origin": Enum-String 用户包期卡来源枚举,
        "originName": String 用户包期卡来源中文,
        "businessType": Enum-String 用户支付业务类型枚举,
        "businessTypeName": String 用户支付业务类型中文,
        "status": Enum-String 用户包期卡状态枚举,
        "statusName": String 用户包期卡状态中文,
		"usableQuota": Number 可以额度,
		"freezedQuota": Number 冻结额度,
		"totalQuota": Number 总额度,
		"payAmount": Number 支付金额,
		"serialNo": String 支付序列号,
		"userPayId": Number 用户支付id,
		"payChannel": Enum-String 支付渠道枚举,
        "payChannelName": String 支付渠道中文,
        "createDateTimeStr": String 购卡时间中文,
        "creatDateTime": DateTime-Number 购卡时间,
        "startDateTimeStr": String 包期卡开通时间中文,
        "endDateTimeStr": String 包期卡结束时间中文,
        "startDateTime": DateTime-Number 包期卡开通时间,
        "endDateTime": DateTime-Number 包期卡结束时间,
        "activeFlag": "YES",
        "version": 8,
      }
    ]
  }
}
```

### 用户包期卡单个查询
- 请求方法： `GET`
- URL：`/userPeriodCard/:id`
- query参数：

| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| id| Number| 是 | 包期卡id | 1 |
- 返回示例：
```javascript
{
  "code": 200,
  "message": "OK",
  "data": {
	    "id": Number 包期卡id,
	    "userId": Number 用户id,
	    "userRealName": String 用户真实姓名,
	    "userNickName": String 用户昵称,
	    "userSex": Enum-String 用户性别枚举,
	    "userSexName": String 用户性别中文,
	    "userMobile": String 用户手机号,
	    "idCardNo": String 身份证,
	    "marketingPeriodCardCategoryId": Number 包期卡类别id,
	    "marketingPeriodCardCategoryType": Enum-String 包期卡类别枚举,
	    "marketingPeriodCardCategoryName": String 包期卡类别中文,
        "origin": Enum-String 用户包期卡来源枚举,
        "originName": String 用户包期卡来源中文,
        "businessType": Enum-String 用户支付业务类型枚举,
        "businessTypeName": String 用户支付业务类型中文,
        "status": Enum-String 用户包期卡状态枚举,
        "statusName": String 用户包期卡状态中文,
		"usableQuota": Number 可以额度,
		"freezedQuota": Number 冻结额度,
		"totalQuota": Number 总额度,
		"payAmount": Number 支付金额,
		"serialNo": String 支付序列号,
		"userPayId": Number 用户支付id,
		"payChannel": Enum-String 支付渠道枚举,
        "payChannelName": String 支付渠道中文,
        "createDateTimeStr": String 购卡时间中文,
        "creatDateTime": DateTime-Number 购卡时间,
        "startDateTimeStr": String 包期卡开通时间中文,
        "endDateTimeStr": String 包期卡结束时间中文,
        "startDateTime": DateTime-Number 包期卡开通时间,
        "endDateTime": DateTime-Number 包期卡结束时间,
        "activeFlag": "YES",
        "version": 8,
      }
}
```

## 商品
  
  
### 商品批量查询
- 请求方法： `GET`
- URL：`/commodity`
- query参数：

| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| page | String | 是 | 请求页码 | 10 请求第10页 |
| limit | String | 是 | 每页数据量 | 10 |
| commodityId| String | 否 | 商品id | 1 |
| commodityName| String | 否 | 商品名称 | 手提包 |
| commodityBrandId| String | 否 | 商品品牌id | 1 |
| series| String | 否 | 系列 | Twist |
| model| String | 否 | 型号 | 中 |
| color| String | 否 | 颜色 | 黑色 |

- 返回示例：
```javascript
{
  "code": 200,
  "message": "OK",
  "data": {
    "count": 419,
    "list": [
     
      {
	    "id": Number 商品id533,
	    "commodityInfoId": Number 商品信息id,
        "no": String 商品货号,
        "name": String 商品名称,
        "series": String 系列,
        "model": String 型号,
        "color": String yanse,
        "commodityCategoryId": Number 商品类别id,
        "commodityCategoryCode": String 商品类别code,
        "commodityCategoryName": Number 商品类型名称,
        "marketPrice": Number 市场价,
        "rentPrice": Number 租赁价,
        "freezedQuota": Number 冻结额度,
        "rentCycle": Enum-String 租赁周期枚举,
        "rentCycleName": String 租赁周期中文,
        "commodityBrandId": Number 商品品牌id,
        "commodityBrandCountry": String 商品品牌国家,
        "commodityBrandNameEn": String 商品品牌英文,
        "commodityBrandNameCn": String 商品品牌中文,
        "commodityBrandLabelIds": String 商品品牌标签id列表,
        "publishFlag": Enum-String 上架标识,
        "recommendDescription": String 推荐描述,
        "introduction": String 商品介绍,
		"introductionImageSrcList":[//商品介绍图片列表
			//String 商品介绍,
		]     
        "src": [//资源路径列表
			String 资源路径,
			]
         "commodityBrandIntroduce": String 商品品牌简介,
        "commodityBrandSrc":[//商品品牌资源路径列表
			String 商品品牌资源路径,
			]
        "commodityBrandLogoSrc": String 商品品牌logo资源路径,
        "activeFlag": "YES",
        "version": 1,
        "totalDiffQuantity": Number 总剩余数量,
        "sizeCwmsCode": {//商品不同规格的cwmscode
          "NM": "000215"
        },
        "sizeDiffQuantity": {//商品不同规格的剩余数量
          "NM": 1
        },
        "commodityLabelList": [//商品标签列表
          {
            "code": String 标签的code,
            "name": String 标签的名称,
            "codeName":String 标签的code中文,
            "id": Number 标签的id
          }
        ],
      }
    ]
  }
}
```

### 商品单个查询
- 请求方法： `GET`
- URL：`/commodity/:id`
- query参数：

| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| id | Number| 是 | 商品id | 221 |

- 返回示例：
```javascript
	{
  "code": 200,
  "message": "OK",
  "data":  {
	    "id": Number 商品id533,
	    "commodityInfoId": Number 商品信息id,
        "no": String 商品货号,
        "name": String 商品名称,
        "series": String 系列,
        "model": String 型号,
        "color": String yanse,
        "commodityCategoryId": Number 商品类别id,
        "commodityCategoryCode": String 商品类别code,
        "commodityCategoryName": Number 商品类型名称,
        "marketPrice": Number 市场价,
        "rentPrice": Number 租赁价,
        "freezedQuota": Number 冻结额度,
        "rentCycle": Enum-String 租赁周期枚举,
        "rentCycleName": String 租赁周期中文,
        "commodityBrandId": Number 商品品牌id,
        "commodityBrandCountry": String 商品品牌国家,
        "commodityBrandNameEn": String 商品品牌英文,
        "commodityBrandNameCn": String 商品品牌中文,
        "commodityBrandLabelIds": String 商品品牌标签id列表,
        "publishFlag": Enum-String 上架标识,
        "recommendDescription": String 推荐描述,
        "introduction": String 商品介绍,
		"introductionImageSrcList":[//商品介绍图片列表
			//String 商品介绍,
		]     
        "src": [//资源路径列表
			String 资源路径,
			]
         "commodityBrandIntroduce": String 商品品牌简介,
        "commodityBrandSrc":[//商品品牌资源路径列表
			String 商品品牌资源路径,
			]
        "commodityBrandLogoSrc": String 商品品牌logo资源路径,
        "activeFlag": "YES",
        "version": 1,
        "totalDiffQuantity": Number 总剩余数量,
        "sizeCwmsCode": {//商品不同规格的cwmscode
          "NM": "000215"
        },
        "sizeDiffQuantity": {//商品不同规格的剩余数量
          "NM": 1
        },
        "commodityLabelList": [//商品标签列表
          {
            "code": String 标签的code,
            "name": String 标签的名称,
            "codeName":String 标签的code中文,
            "id": Number 标签的id
          }
       ]
   }
}
```
## 商品品牌
  
  
### 商品品牌批量查询
- 请求方法： `GET`
- URL：`/commodityBrand`
- query参数：

| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |

- 返回示例：
```javascript
	{
  "code": 200,
  "message": "OK",
  "data": [
    
    {
	  "id": Number 品牌id,
      "country": String 品牌国家,
      "nameCn": String 品牌中文名字,
      "nameEn": String 品牌英文名字,
      "logoSrc": String 品牌logo路径"/commodityBrand/Tod's/Tod's.png",
      "src": [//品牌资源路径列表
			String 品牌资源路径
		],
      "introduce": String 品牌简介,
      
      "labelIds":[//品牌标签id列表
		String 品牌标签id,
		]
      "labelList": [//品牌标签详细
        {
          "code": String 标签code,
          "name": String 标签名字,
          "codeName": String 标签code名字,
          "id": 标签code
        },
        
      ],
      "activeFlag": "YES",
      "version": 1,
      
      
      
      
      
      
      
    }
  ]
}
```


## 系统菜单
### 根据系统用户id查询用户拥有的菜单
- 请求方法： `GET`
- URL：`/sysuser/menu/:id`
- query参数：

| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| id | Number| 是 | 系统用户id | 1|

- 返回示例：
```javascript
{
  "code": 200,
  "message": "OK",
  "data": [
    {//一级菜单
	  "name": String 菜单名称,
      "id": Number 菜单id,
      "url": String 菜单url,
      "children": [//二级菜单列表
        {
	      "name": String 菜单名称,
	      "id": Number 菜单id,
	      "url": String 菜单url,
          "children": [//三级菜单
            {
              "name": String 菜单名称,
		      "id": Number 菜单id,
		      "url": String 菜单url,
            }
          ],
        },
      ],
    },
  ]
}
```