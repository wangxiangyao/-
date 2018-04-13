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
  
- type(用户类型)
  
|  key      |    Value | 
| :-------- | :--------:| 
|  COMMON | 普通会员 |  
|  EXPERIENCE     |   体验卡会员 | 
|  TWO_STAR      |    双星卡会员 | 
|  FOUR_STAR      |    四星卡会员 | 
|  SIX_STAR      |    六星卡会员 | 
  
- realNameAuthStatus(实名认证状态)
  
|  key      |    Value | 
| :-------- | :--------:| 
|  NO_AUTH | 未认证 |  
|  IN_AUTH     |   认证中 | 
|  AUTH_SUCCESS      |    认证成功 | 
|  AUTH_FAIL     |   认证失败|
  
- marketingPeriodCardCategoryType(包期卡类别)
  
|  key      |    Value | 
| :-------- | :--------:| 
|  EXPERIENCE | 体验卡 |  
|  TWO_STAR     |   双星卡 | 
|  FOUR_STAR      |    双星卡 | 
|  SIX_STAR     |   六星卡|
  
- origin(包期卡来源)
  
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
  
- status(用户包期卡状态)
  
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
-  status(订单状态)

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
| 500	|	系统异常 |
|1001	|账号或者密码错误|
|1002	|查询参数错误|
  
  
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
- URL：`/users`
- query参数：
  
| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| page | Number | 是 | 请求页码 | 10 请求第10页 |
| limit | Number | 是 | 每页数据量 | 10 |
| id | Number | 否 | 用户id | 1 |
| nickName | String | 否 | 用户昵称 | 布雷布雷 |
| sex | Enum-String | 否 | 性别：MALE(男)，FEMALE(女) | MALE |
| registerTime | [DateTime-number, DateTime-number] | 否 | 注册时间区间 [开始，结束] 0表示不限制 | [0, 1523242919345], [1523242919345, 0] |
| isPeriod | Boolean | 否 | 是否为包期卡用户 | true |
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
        id: Number 用户id
        registerTime: DateTime-Number 注册时间
        registerTimeStr:String 注册时间字符串(yyyy-MM-dd HH:mm:ss)
        nickName: String 昵称 
        sex: Enum-String 性别 
        idCardNo: String 身份证
        mobile：String 手机号
        type：Enum-String 用户类型
        realNameAuthStatus: Enum-String 用户是否实名认证
        realName：String 真实姓名
        shareOriginChannel: String 通过哪个渠道进入
      }
      ...
    ]
  }
}
  
// and so on
```
  
### 单个查询
  
  
- 请求方法：`GET`
- URL：`/users/:id`
- URL参数
  
| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| id | Number | 是 | 用户id | 1 | 
  
- 返回示例：
```javascript
{
  code: 200,
  message: 'ok',
  data: {
    id: Number 用户id
    registerTime: DateTime-Number 注册时间
    nickName: String 昵称 
    sex: Enum-String 性别 
    idCardNo: String 身份证 
    mobile：String 手机号 
    type：Enum-String 用户类型
    realNameAuthStatus: Enum-String 用户是否实名认证
    realName：String 真实姓名
    shareOriginChannel: String 通过哪个渠道进入
  
    // 详细信息？？？
    addressList: {
      count
      list: [
		{
        id: Number 地址id,
        userId: Number 地址所属用户id
        defaultFlag: Enum-String: "NO" "YES"
        name：String 收件人姓名
        mobile：String 收件人手机号
  
        mostSuperiorCommonAreaName：String 一级地址
        parentCommonAreaName：String 二级地址
        commonAreaName: String 三级地址
  
        mostSuperiorCommonAreaNameId：Number 一级地址id
        parentCommonAreaNameId：Number 二级地址id
        commonAreaNameId：Number 三级地址id
  
        address： String 街道地址
		}
      ]
    },
    periodCardList: {
      count
      list: [
	  {
        id: Number 包期卡id
        userId: Number 包期卡所属用户id
        version: Number 解决并发修改问题
        serialNo: String 包期卡序列号 
        description: 包期卡描述
        marketingPeriodCardCategoryType: Enum-String: "SIX_STAR" 包期卡的类型的英文
        marketingPeriodCardCategoryId: Number 包期卡类型的id
  
        userPayId: Number 支付包期卡的支付凭证id
        transferFromUserId: Number 转增人
        origin: Enum-String: "BUY_BY_USER" 没有列全
        originName: String 来源中文
        payAmount: Number 支付金额
        payChannel: Enum-String "WEIXIN" 支付方式英文 没有列全
        payChannelName: Enum-String: "微信", ""  支付渠道
        bussinessType: Enum-String "PERIOD_CARD_NEW_PAY" 商业类型英文
        businessTypeName: String 商业类型
  
        status： Enum-String 状态 没有列全
        statusName: String 开启状态
  
        freezedQuota: Number 冻结金额
        usableQuota: Number 可用额度
        totalQuata: Number 总额度
  
        开发时间
        激活时间
        到期时间
		}
      ]
    },
    purchaseList: {
      count
      list: [{
        "rentCycleName": String,租赁周期中文
        "freezedQuota": Number,冻结额度
        "rentMethodName": String,租赁方式中文
        "payTotalAmount": Number,支付总金额
        "rentMethod": Enum-String ,租赁方式
        "commodityId": Number, 商品id
        "payDeposit": Number,支付押金
        "userId": Number,用户id
        "payRentAmount": Number,支付租金
        "rentCycle": Enum-String,租赁周期
        "purchaseNo": String,订单编号
        "id": Number,订单id
        "rentPrice": Number,租赁价格
        "usedIntegral": Number,使用积分
        "commodityName": String 商品名称
	  }]
    }
  }
}
  // and so on
```
## 订单
  
  
### 批量查询
- 请求方法： `GET`
- URL：`/purchases`
- query参数：

| 参数名 | 类型 | 是否必须 | 描述 | 示例 |
| ---    | --- | --- | --- | --- |
| page | Number | 是 | 请求页码 | 10 请求第10页 |
| limit | Number | 是 | 每页数据量 | 10 |
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
|status	|Enum-String|否|订单状态|详情见枚举的说明|

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

### 单个查询
  
  
- 请求方法：`GET`
- URL：`/users/:id`
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