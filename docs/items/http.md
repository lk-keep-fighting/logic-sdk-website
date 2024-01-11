---
sidebar_position: 30
---

# http请求

:::tip

用于实现请求http接口

:::

## 配置说明

### 请求URL
通过return字符串实现url的灵活动态配置。
```js

return _env.HOST + '/api/pay'

```
### 请求类型
http的请求method。
### 请求头headers
与URL配置同理，返回需要的headers
```js
return {
    'token': _env.token,
    'devceId':'110111'
}
```
### body请求参数
与URL配置同理，返回需要的body
```js
return {
    'a': _par.a,
    'from':'logic'
}
```
### 将response.data赋值给哪个参数
可以将http请求的返回数据直接赋值给局部变量，方便后续处理
```js
_var.repData

```
### 执行超时设置(ms)
设定请求超时时间，单位毫秒，超时则报错。
