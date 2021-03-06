## 通用内容
### 响应数据格式
```json
{
    "errorMsg": "请求成功",
    "errorCode": 0,
    "data": {
        "name": "name",
        "id": 1
    }
}
```
- errorCode : 响应码，0 代表请求成功，其他数值代表请求失败。
- errorMsg : 响应失败信息。
- data : 请求的数据。

### 查询与添加
- 查询：默认使用 get 方法。
- 添加：默认使用 post 方法，添加内容时需要验证用户权限，在 header 中添加 id 字段，传入用户 id 。

## 查询 & 添加
- 查询会用到多表拼接，数据类型，比单一的表字段要多；
- 添加只会用到单一表格的数据。
- 关于数据对象  
为了偷懒，查询和添加会使用相同的数据类型，但是，在添加数据库数据时，会冲突。
- 解决方法
  - 在 Gson 生成 json 数据时，所有为 null 的对象都会被忽略掉。利用这个特性，就可以解决冲突，
  在类里面添加一个提交前初始化的方法，把不相关数据置空。
  - 在定义对象类型的时候，使用基本数据类型对应的类代替基本数据类型。
