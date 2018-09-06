---
title: API设计规范
date: 2018-05-22 11:52:51
tags:
---

## API 地址和版本
    
* 比如 https://api.github.com/v3；也可以简单地把版本放在路径中，比如 https://example.com/api/v1
* 一般均使用URL/{UID}/1
* 如遇到筛选可使用query_string ?XX=XX&XX=XX
*  url小写

##  使用正确的 Method

<table>
  <thead>
    <tr>
      <th>Verb</th>
      <th>描述</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>HEAD</td>
      <td>只获取某个资源的头部信息。比如只想了解某个文件的大小，某个资源的修改日期等</td>
    </tr>
    <tr>
      <td>GET</td>
      <td>获取资源</td>
    </tr>
    <tr>
      <td>POST</td>
      <td>创建资源</td>
    </tr>
    <tr>
      <td>PATCH</td>
      <td>更新资源的部分属性。因为 PATCH 比较新，而且规范比较复杂，所以真正实现的比较少，一般都是用 POST 替代</td>
    </tr>
    <tr>
      <td>PUT</td>
      <td>替换资源，客户端需要提供新建资源的所有属性。如果新内容为空，要设置 <code class="highlighter-rouge">Content-Length</code> 为 0，以区别错误信息</td>
    </tr>
    <tr>
      <td>DELETE</td>
      <td>删除资源</td>
    </tr>
  </tbody>
</table>


## 其他

- 不符合 CRUD 的情况使用POST
- [API设计中时间定义的5条规则](https://blog.csdn.net/yfkiss/article/details/51944275)
- [跟着 Github 学习 Restful HTTP API 设计](https://segmentfault.com/p/1210000008733982/read)

## API http code约定

- 200 get查询请求成功
- 201 [POST/PUT/PATCH]用户新建或修改数据成功
- 204 [DELETE]：用户删除数据成功
- 404 get查询失败（也表示获得授权但是被禁止访问，此时用404代替403）
- 422 增删改查失败（查特指参数错误）
- 400 INVALID REQUEST - [POST/PUT/PATCH]：用户发出的请求有错误，服务器没有进行新建或修改数据的操作，该操作是幂等的。
- 401 表示用户没有权限（令牌、用户名、密码错误（需要鉴权）
- 405 请求方式错误
- 409 资源冲突
- 500 服务器错误（其他异常）

