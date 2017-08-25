---
layout: page
title: My Gallery
tags:
  - js
  - php
  - node
  - 随笔
  - 日常
---

## 功能需求
1. 获取菜单数据[[01](#j01)]
2. 添加菜单数据[[02](#j02)]
3. 修改菜单数据[[03](#j03)]
4. 删除菜单数据[[04](#j05)]
5. 获取分类[[05](#j05)]
6. 添加分类[[06](#j06)]
7. 修改分类[[07](#j07)]
8. 删除分类[[08](#j08)]

<!-- more -->
### <span id = "j01"> 01 - 获取菜单数据　</span>
**简要描述：** 

- 获取商家菜单模板数据

**请求URL：** 

- ` ./template.json?type=catering&csrf_token=xxx&is_tpl=1 `
  
**请求方式：**
- GET 

** 请求参数： ** 

| 参数名 | 必需 | 类型 | 说明 |
| :----: | :---: | :-----: | :-----: |
| csrf_token | 是 | string | token |
| type | 是 | string | catering点餐 virtual代充 |
| is_tpl | 是 | int | 固定值 1 |

 **返回示例**

``` 
{
  "count":26,
  'page':3,
  'data':[
        {'_id':'xxx','title':'农家小炒肉','cat_name':'套餐','price':1800,'desc':'好吃巴适','thumb':'xxx'},
        {'_id':'xxx','title':'农家小炒肉','cat_name':'套餐','price':1800,'desc':'好吃巴适','thumb':'xxx'},
        ...
   ]
  }
```

 ** 返回参数说明 ** 

| 参数名 | 类型 | 说明 |
| :----: | :---: | :-----: |
| title | string | 名称 |
| cat_name | string | 分类名 |
| price | int | 价格.单位:分 |
| desc | string | 描述备注 |
| thumb | string |图片 |


### <span id = "j02"> 02 - 添加菜单数据　</span>
**简要描述：** 

- 添加新的点餐数据

**请求URL：** 
- ` ./template.json?type=catering&csrf_token=xxx&is_tpl=1 `
  
**请求方式：**
- POST 

** 请求参数： ** 

| 参数名 | 必需 | 类型 | 说明 |
| :----: | :---: | :-----: | :-----: |
| csrf_token | 是 | string | token |
| type | 是 | string | catering点餐 virtual代充 |
| title | 是 | string | 名称 |
| cat_id | 是 | string | 分类id |
| price | 是 | string | 餐单价格.必须大于0 |
| thumb | 否 | string | 菜单图片 |
| desc | 否 | string | 备注说明 |
| is_tpl | 是 | int | 固定值 1 |

 **返回示例**

``` 
{
  '_id':'xxx',
  'title':'农家小炒肉',
  'cat_name':'套餐',
  'price':1800,
  'desc':'好吃巴适',
  'thumb':'xxx'
}
```

 ** 返回参数说明 ** 

- 同上


### <span id = "j03"> 03 - 修改数据　</span>
**简要描述：** 

- 修改已有的点餐数据

**请求URL：** 
- ` ./template.json?&csrf_token=xxx `
  
**请求方式：**

- PUT 

** 请求参数： ** 

| 参数名 | 必需 | 类型 | 说明 |
| :----: | :---: | :-----: | :-----: |
| csrf_token | 是 | string | token |
| id | 是 | string | 当前数据的id |
| title | 否 | string | 名称 |
| cat_id | 否 | string | 分类id |
| price | 否 | string | 餐单价格.必须大于0 |
| thumb | 否 | string | 菜单图片 |
| desc | 否 | string | 备注说明 |

- 只提交修改的字段

 **返回示例**

``` 
{
  '_id':'xxx',
  'title':'农家小炒肉',
  'cat_name':'套餐',
  'price':1800,
  'desc':'好吃巴适',
  'thumb':'xxx'
}
```

 ** 返回参数说明 ** 

- 同上


### <span id = "j04"> 04 - 删除数据　</span>
**简要描述：** 

- 删除已有的点餐数据

**请求URL：** 
- ` ./template.json?&csrf_token=xxx `
  
**请求方式：**

- DELETE 

** 请求参数： ** 

| 参数名 | 必需 | 类型 | 说明 |
| :----: | :---: | :-----: | :-----: |
| csrf_token | 是 | string | token |
| id | 是 | string | 删除的数据id.多条使用数组 |

- 只提交修改的字段

 **返回示例**

``` 
{
  'id':{'xxx','bbb'}
}
```

 ** 返回参数说明 ** 
 
| 参数名 | 类型 | 说明 |
| :----: | :---: | :-----: |
| id | string | 删除成功的数据id[s] |



### <span id = "j05"> 05 - 获取分类　</span>
**简要描述：** 

- 获取分类

**请求URL：** 
- ` ./template/getcats.json?csrf_token=xxx&type=xxx `
  
**请求方式：**

- GET 

** 请求参数： ** 

| 参数名 | 必需 | 类型 | 说明 |
| :----: | :---: | :-----: | :-----: |
| csrf_token | 是 | string | token |
| type | 否 | string | catering点餐 virtual代充. 默认餐点分类 |

 **返回示例**

``` 
[{
  {'id':'xxx','name':'腾讯'},
  {'id':'xxx','name':'网易'},
  ...
}]
```

 ** 返回参数说明 ** 
 
| 参数名 | 类型 | 说明 |
| :----: | :---: | :-----: |
| id | string | 分类id |
| name | string | 分类名称 |



### <span id = "j06"> 06 - 添加分类　</span>
**简要描述：** 

- 添加新分类

**请求URL：** 
- ` ./template/addcat.json?&csrf_token=xxx `
  
**请求方式：**

- POST 

** 请求参数： ** 

| 参数名 | 必需 | 类型 | 说明 |
| :----: | :---: | :-----: | :-----: |
| csrf_token | 是 | string | token |
| name | 是 | string | 分类名称 |
| is_tpl | 是 | int | 固定值 1 |


 **返回示例**

``` 
{
  '_id':'xxx',
  'name':'腾讯'
}
```

 ** 返回参数说明 ** 
 - 同上


### <span id = "j07"> 07 - 修改分类　</span>
**简要描述：** 

- 修改分类名称

**请求URL：** 
- ` ./template/upcat.json?id=xxx&csrf_token=xxx `
  
**请求方式：**

- PUT 

** 请求参数： ** 

| 参数名 | 必需 | 类型 | 说明 |
| :----: | :---: | :-----: | :-----: |
| csrf_token | 是 | string | token |
| name | 是 | string | 分类名称 |
| id | 是 | string | 数据id |

 **返回示例**

``` 
{
  'id':'xxx',
  'name':'腾讯'
}
```

 ** 返回参数说明 ** 
 
 - 同上


### <span id = "j08"> 08 - 删除分类　</span>
**简要描述：** 

- 修改分类名称

**请求URL：** 
- ` ./template/delcat.json?&csrf_token=xxx `
  
**请求方式：**

- DELETE

** 请求参数： ** 

| 参数名 | 必需 | 类型 | 说明 |
| :----: | :---: | :-----: | :-----: |
| csrf_token | 是 | string | token |
| id | 是 | string | 删除的数据id |

 **返回示例**

``` 
{
  'id':'xxx',
}
```

 ** 返回参数说明 ** 
 
 - 同上
