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
  
- 协议基于HTTPS（此处待议）
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
  
  
  
  