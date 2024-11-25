# 自定义TTS

## 请求示例

```javascript
// 请求地址
let url = 'https://www.baidu.com'; 

// 请求参数
let params = {
	type: 'zh-linzhilin',
	text: '你好，世界！'
};

// 请求header
let header = {
	token: 'xxx'	
};

// POST请求，具体参考文档 native-to-js
let response = await app.post({
	url,
	params,
	header
});

// 如果responseBody是一个json字符串
let json = app.stringToJson(response.responseBody);

// 获取到语音文件的地址
let voiceUrl = json.url;

return {
	url: voiceUrl, // 语音请求地址
	method: 'GET', // 请求方式
	params: {}, // 携带的参数
	header: {}, // 携带的header
	cookie: {} // 携带的cookie
};
```