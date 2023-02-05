# 编码中如何使用浏览器

## 获取请求参数
获取请求的入参数，出参，获取CURL的请求命令等

## 重试发起请求
通过"Replay XHR"功能重新发起GET请求
```js
fetch("https://5fu8.com/search.json?a=abc", {
  "referrerPolicy": "strict-origin-when-cross-origin",
  "body": null,
  "method": "GET"
}).then(res => res.json())
.then(txt => console.log(JSON.stringify(txt)))
```

## 常用的一些函数
### 日期转换
```js
new Date('2023-02-04 11:22:33')
new Date('2023-02-04 11:22:33').getTime()
```

### 打开新网页
```js
window.open('https://5fu8.com')
/*获取页面来源地址*/
document.referrer
```
### 浏览器解码与编码
```js
decodeURIComponent('https://5fu8.com/?a=%E4%BD%A0%E5%A5%BD')
encodeURIComponent('https://5fu8.com')
```