## 1、接收合作方现有登录态【阅文】 {#jieshoudenglutai}

### 1.1 说明 {#第一个}

接收合作方现有登录态的ticket，用于用户无感知登录。

### 1.2请求

方向：合作方-&gt;阅文开放平台H5

协议:https

方法: get

url地址：[https://xxx.yuewen.com/xxxx/xxxx.html?\_cptoken=xxxxxxxx](https://xxx.yuewen.com/xxxx/xxxx.html?_cptoken=xxxxxxxx)

备注：阅文H5站点的任意页面均可接收此参数

### 1.3输入参数

| 参数名称 | 类型 | 必填 | 示例值 | 备注 |
| :--- | :--- | :--- | :--- | :--- |
| \_cptoken | String\(128\) | N | XXXX | 此token由合作方生成，规则可自定义 |

### 1.4返回参数

无

## 2、用户登录URL【合作方】 {#userlogin}

### 2.1说明

用户登录URL。

### 2.2请求

协议:https/http

方法: get

url地址：合作方提供

### 2.3阅文侧提供的输入参数

| 参数名称 | 类型 | 必填 | 示例值 | 备注 |
| :--- | :--- | :--- | :--- | :--- |
| appflag | string | N | yuewen | 合作方在阅文开放平台的唯一标识 |
| redirect\_uri | string | Y |  | 登陆后回调地址，UrlEncode |
| state | String | Y |  | 用于保持请求和回调的状态，d登录完成后需原样返回。该参数可用于防止csrf |

### 2.4返回参数

无

## 3、登录回调接口【阅文】

### 3.1说明

发起合作方登录，完成登录后回调地址，用于处理用户主动登录。

### 3.2请求

方向：合作方-&gt;阅文开放平台H5

协议:https

方法: get

url地址：[https://mcp.yuewen.com/mcp/cplogin/logincallbac?appflag=yuewen&\_cptoken=xxxxxxxx&state=xxxx](https://mcp.yuewen.com/mcp/cplogin/logincallbac?appflag=yuewen&_cptoken=xxxxxxxx&state=xxxx)

### 3.3输入参数

| 参数名称 | 类型 | 必填 | 示例值 | 备注 |
| :--- | :--- | :--- | :--- | :--- |
| appflag | String | Y | yuewen | 合作方在阅文开放平台的唯一标识 |
| \_cptoken | String | Y |  | 此ticket由合作方生成，规则可自定义 |
| state | String | Y |  | 发起登录时传递的值原样返回 |

### 3.4返回参数

无

## 4、获取用户信息接口【合作方】

### 4.1说明

请求合作方服务端获取用户信息。

### 4.2请求

方向：阅文开放平台服务端-&gt;合作方服务器

协议:https/http

方法: get

url地址：合作方提供

### 4.3输入参数

| 参数名称 | 类型 | 必填 | 示例值 | 备注 |
| :--- | :--- | :--- | :--- | :--- |
| \_cptoken | string | Y |  | 接口1和接口3返回的cptoken |
| appflag | String | Y |  | 合作方在阅文开放平台的唯一标识 |

### 4.4 输出参数\[JSON\]

| 参数名称 | 类型 | 必填 | 示例值 | 备注 |
| :--- | :--- | :--- | :--- | :--- |
| code | int | Y | 0 | 0成功，非0失败。 |
| msg | String | N | 成功 | 对code的中文描述 |
| data | Array | Y |  |  |
| openid | String | Y | 111 | 合作方唯一用户id |
| nickname | String | Y | 张小花 | 用户在合作方平台的昵称 |
| avatar | String | Y |  | 用户头像URL，建议可拼接多规格 |

### 4.5 返回数据示例

{

"code": 0,

"msg": "成功",

"data": {

"openid": "22099347000501502",

"nickname": "张小花",

"avatar": "[http://img1.chuangshi.qq.com/upload/avatar/2016-04-05/57036b9923011.jpeg](http://img1.chuangshi.qq.com/upload/avatar/2016-04-05/57036b9923011.jpeg)"

}

}

