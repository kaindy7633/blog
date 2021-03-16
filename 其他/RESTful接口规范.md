# RESTful接口规范概要

## 协议

使用 http/https 协议

## 版本

将 `API` 的版本号放入 `URL`，如 https://github.com/kaindy7633/v1/

## HTTP动词

- `GET`（`SELECT`）：从服务器取出资源（一项或多项）。
- `POST`（`CREATE`）：在服务器新建一个资源。
- `PUT`（`UPDATE`）：在服务器更新资源（客户端提供改变后的完整资源）。
- `PATCH`（`UPDATE`）：在服务器更新资源（客户端提供改变的属性）。
- `DELETE`（`DELETE`）：从服务器删除资源。

## 路径

每个网址代表一种资源（`resource`），所以网址中不能有动词，只能有名词

- URI中的名词表示资源集合，使用复数形式
- 不用大写
- 用中杠 `-`, 不用下杠 `_`
- 参数列表要 `encode`

## 状态码

- `200 OK` - [`GET`]：服务器成功返回用户请求的数据，该操作是幂等的（`Idempotent`）
- `201 CREATED` - [`POST/PUT/PATCH`]：用户新建或修改数据成功。
- `202 Accepted` - [`*`]：表示一个请求已经进入后台排队（异步任务）
- `204 NO CONTENT` - [`DELETE`]：用户删除数据成功。
- `400 INVALID REQUEST` - [`POST/PUT/PATCH`]：用户发出的请求有错误，服务器没有进行新建或修改数据的操作，该操作是幂等的。
- `401 Unauthorized` - [`*`]：表示用户没有权限（令牌、用户名、密码错误）。
- `403 Forbidden` - [`*`] 表示用户得到授权（与 `401`错误相对），但是访问是被禁止的。
- `404 NOT FOUND` - [`*`]：用户发出的请求针对的是不存在的记录，服务器没有进行操作，该操作是幂等的。
- `406 Not Acceptable` - [`GET`]：用户请求的格式不可得（比如用户请求 `JSON` 格式，但是只有 `XML` 格式）。
- `410 Gone` -[`GET`]：用户请求的资源被永久删除，且不会再得到的。
- `422 Unprocesable entity` - [`POST/PUT/PATCH`] 当创建一个对象时，发生一个验证错误。
- `500 INTERNAL SERVER ERROR` - [`*`]：服务器发生错误，用户将无法判断发出的请求是否成功。

`1xx` 范围的状态码是保留给底层 `HTTP` 功能使用的，并且估计在你的职业生涯里面也用不着手动发送这样一个状态码出来。

`2xx` 范围的状态码是保留给成功消息使用的，你尽可能的确保服务器总发送这些状态码给用户。

`3xx` 范围的状态码是保留给重定向用的。大多数的 `API` 不会太常使用这类状态码，但是在新的超媒体样式的 `API` 中会使用更多一些。

`4xx` 范围的状态码是保留给客户端错误用的。例如，客户端提供了一些错误的数据或请求了不存在的内容。这些请求应该是幂等的，不会改变任何服务器的状态。

`5xx` 范围的状态码是保留给服务器端错误用的。这些错误常常是从底层的函数抛出来的，并且开发人员也通常没法处理。发送这类状态码的目的是确保客户端能得到一些响应。收到 `5xx` 响应后，客户端没办法知道服务器端的状态，所以这类状态码是要尽可能的避免。

## 国际化

在 `HTTP` 请求 `Header` 中, 携带 `Accept-Language` 字段, 表明当前要使用的语言, 如:

`Accept-Language: zh-CN`

以下是常用语言:

| 字段 | 值 |	说明 |
| ---- | --- | --- |
| `Accept-Language` |	`zh-CN` |	简体中文 |
| `Accept-Language` |	`zh-TW` |	繁体中文 |
| `Accept-Language` |	`en-US` |	英文 |

## 处理错误

所有错误可以在 `HTTP` 请求处, 统一处理

- 发生错误时, 状态码大于 `400`; 只有当状态码位于 `200-300` 区间时, 请求才成功
- 状态码为 `400`, `404`, `403`, `406`, `500` 返回的 `JSON` 信息中, `message` 为错误信息,如

```json
{
   "message":"验证失败_内容不能为空"
}
```

- 状态码为 `422` (验证失败)时返回的信息为一个对象数组, 每个对象中包含 `field` 和`message`信息, 如

```json
[
    {
        "field": "verify_code",
        "message": "短信验证码不正确"
    },
    {
        "field": "phone",
        "message": "手机号已被注册"
    }
]
```

## 调试

所有 `API` 请求结果的 `Header` 中携带 `X-Debug-Tag` 参数,该参数为请求的 `id`
调试时, 打开 `/debug` 网址, 然后使用 `debug-tag` 过滤找到相应的请求

## 返回结果

- `GET /collection`：返回资源对象的列表（数组）
- `GET /collection/resource`：返回单个资源对象
- `POST /collection`：返回新生成的资源对象
- `PUT /collection/resource`：返回完整的资源对象
- `PATCH /collection/resource`：返回完整的资源对象
- `DELETE /collection/resource`：返回一个空文档

## 数据格式

只用以下常见的 `body format`：

- `Content-Type: application/json` (`API`使用的格式)
- `Content-Type: application/x-www-form-urlencoded` (浏览器 `POST` 表单用的格式)

## API携带超链接

返回结果中提供链接，连向其他 `API` 方法，使得用户不查文档，也知道下一步应该做什么

```json
{"link": {
  "rel":   "collection https://www.example.com/zoos",
  "href":  "https://api.example.com/zoos",
  "title": "List of zoos",
  "type":  "application/vnd.yourformat+json"
}}
```

上面代码表示，文档中有一个 `link` 属性，用户读取这个属性就知道下一步该调用什么 `API`了。 

`rel`表示这个 `API` 与当前网址的关系（`collection` 关系，并给出该 `collection` 的网址）

`href` 表示 `API` 的路径，`title` 表示 `API` 的标题，`type` 表示返回类型。

## 参考链接

- [RESTful API设计指南-阮一峰](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)
- [Restful API的设计规范](http://novoland.github.io/%E8%AE%BE%E8%AE%A1/2015/08/17/Restful%20API%20%E7%9A%84%E8%AE%BE%E8%AE%A1%E8%A7%84%E8%8C%83.html)
- [好RESTful API的设计原则](https://www.cnblogs.com/moonz-wu/p/4211626.html)
- [HTTP API 设计指南](https://github.com/cocoajin/http-api-design-ZH_CN)
- [HTTP 接口设计指北](https://github.com/bolasblack/http-api-guide)
- [RESTful API 设计参考文献列表](https://github.com/aisuhua/restful-api-design-references)