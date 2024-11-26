# 前置请求
什么是前置请求？在正式请求之前处理的请求统称前置请求。比如在搜索时，搜索关键字被加密了，那就需要前置请求来处理加密的内容。

- 前置请求与正式请求最大的区别在于前置请求拥有一个Put参数，该参数主要用于将获取的数据进行存储，然后在正式请求中使用。

## PUT存储案例

### xpath规则进行获取
```json
// 从前置请求的页面中获取2个参数，一个命名为name，一个命名为test
{
    'name': '//*[@class="name"]/text()',
    'test': '//*[@class="text"]/text()'
}
```

### JSONPATH规则获取
```json
// 从前置请求的json中获取info信息，info如果是一个对象，则会直接存储该对象
{
  'info': '$.info'
}
```

## 正式请求获取案列

比如现在在正式请求的请求信息中编写JS代码

```javascript
// 获取存储的name
let name = '@get{name}';

//获取存储的test
let test = '@get{test}';

// 获取jsonpath的数据，如果info为对象，则可以使用info.name获取它的子集
let name = '@get{info.name}'

```

也可以在规则字段中使用，比如在搜索的规则字段：搜索请求url
```
http://www.xxx.com/?keyword=@get{name}
http://www.xxx.com/?keyword=@get{info.name}
```