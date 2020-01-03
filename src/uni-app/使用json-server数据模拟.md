1、项目根目录下创建server文件夹

```
mkdir server
```

2、server文件夹下创建数据模拟文件

```
cd server && touch db.json
```

2.1、文件格式与服务端格式保持一致

```
{
    example:{
        "code": "SUCCESS",
        "msg": "成功"，
        "data":{}
    },
    example2:{
        "code": "SUCCESS",
        "msg": "成功"，
        "data":{}
    }
}
```

3、server文件夹下创建路由映射文件

```
touch routes.json
```

3.1、[其他用法详见](<https://github.com/typicode/json-server>)

```
{
    "/api/*": "/$1",
    "/:resource/:id/show": "/:resource/:id",
    "/posts/:category": "/posts?category=:category",
    "/articles\\?id=:id": "/posts/:id"
}
```

4、运行接口服务器

```
json-server --watch db.json --routes routes.json -H 192.168.1.1
```

5、接口资源以db.json内容自动生成api链接

```
 http://192.168.11.165:3000/example
 http://192.168.11.165:3000/example2
```

根据路由映射，以下链接同样有效

```
http://192.168.11.165:3000/api/example
http://192.168.11.165:3000/api/example2
```



