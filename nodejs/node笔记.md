# package_one

## fs文件系统模块
    fs.readFile()文件读取
    
    fs.writeFile()文件写入 可以创建文件但是不能创建目录 多次使用方法写入一个文件，后写入的会覆盖先写入的

    _ _dirname表示当前文件所属目录

## path模块

    path.join()可以将字符串拼成一个完整的路径

    ../会抵消前面的路径,可以获取上个目录路径的文件

    文件的路径最好不要用+来进行拼接

    使用path.join(__dirname, '文件路径')

    path.basename(path,ext)获取路径中的最后一部分，通常使用这个方法获取文件名

    path <string> 必选参数，表示一个路径的字符串

    ext <string> 可选参数，表示文件扩展名

    如果不适用ext会返回连带着扩展名的文件名，如果使用ext那么不会返回扩展名,前提是ext参数和所获取的文件扩展名后缀一致

    path.extname(path)可以获取路径中扩展名部分

## 小实验拆解html文件 （package_two项目）

    index.js nodejs执行文件

    index.html 拆解前html文件

    main.css 拆解后css文件

    main.js 拆解后js文件

    main.html 拆解后html文件

## http模块
    在网络节点中，负责消费资源的电脑叫做客户端，负责对外提供网络资源的电脑叫做服务器

## ip地址

    ip地址相当于互联网上每台电脑的唯一标识,只有在知道对方ip地址的情况下，才能与对应的电脑进行数据通信

    ip地址的格式通常用点分十进制表示成(a.b.c.d)的形式，其中a,b,c,d都是在0~255之间的十进制整数

## 域名
    ip地址的别名

    域名与ip是一一对应的关系，这种对应关系存放在域名服务器中(DNS，Domain name server),使用者只需记好域名访问对应的服务器即可，对应的转换工作由DNS实现

## 端口号

    端口号是电脑中web服务的唯一标识，通过端口号可以准确的将请求交给对应的web服务来处理

    每个端口号同时只能被一个web服务使用

    在url中8080端口可以被省略，其他的不可以

## 创建web服务的基本步骤

    1、导入http模块

    2、创建web服务器实例 http.createServer()

    3、为服务器实例绑定request时间，监听客户端请求 server.on('request' , (req,res) => {})

        1）req请求对象

            req中包含了与客户端有关的数据和属性 如：req.url 客户端请求的URL地址、req.method 客户端的method请求方法

        2）res响应对象

            在服务器的request事件处理函数中，如果想访问与服务器有关的数据与属性，可以使用res 如res.end() 向客户端发送指定内容并结束请求
            在使用res.end(data)向客户端返回中文的时候会发生乱码，这个时候需要设置响应头 Content-type的值为 text/html;charset=urf-8
            使用res.setHeader()来设置响应头

    4、启动服务器 server.listen(8080,() => {})

## 根据不同的url相应不同的html内容

    1、获取请求的url地址

    2、设置默认的相应内容为404 Not found

    3、判断用户请求的是否为/或/index.html首页

    4、判断用户请求的是否为/about关于页面

    5、设置Content-Type响应头，防止中文乱码

    6、使用res.end()把内容相应给客户端

## 模块化
    模块化是指在解决一个复杂问题时，自顶向下逐层把系统划分为若干模块的过程。对于整个系统来说，模块是可组合、分解和更换的单元

    变成领域的模块化，就是遵守规定的规则，把一个大文件拆成独立并互相依赖的小文件

    把代码进行模块化拆分的好处：

        提高了代码的复用性

        提高了代码的可维护性

        可以实现按需加载

## 模块化规范
    模块化规范就是对代码进行模块化拆分与组合时，需要遵守的规则，比如引用模块和暴露模块

## nodejs中的模块化规范
    nodeJs遵循了CommonJs模块化规范，CommonJs规定了模块的特性和各模块之间如何相互依赖

    CommonJs规定：

        每个模块的内部，module变量代表当前模块

        module变量是一个对象，他的exports属性是对外的接口

        加在某个模块，其实是加载该模块的module.exports属性。require方法用于加载模块

## nodejs中的模块的分类
    1、内置模块（内置模块是由Node.js观风提供的，如 fs、path、http等）

    3、自定义模块 （用户创建的每个js文件，都是自定义模块）

    4、第三方模块 （由第三方开发的模块，并非官方提供的内置模块，也不是用户创建的自定义模块，使用前需先下载）

### 加载模块
    使用require()可以加载需要的内置模块，自定义模块，第三方模块进行使用

    注意：使用require()方法加载其他模块时，会执行被加载模块中的代码


## nodejs中的模块作用域
    在自定的模块中定义的变量、方法只能在当前模块使用

    好处：

        可以防止全局变量污染

## 向外共享模块作用域中的成员
    再每个js自定义模块中都有一个module对象，它里面存储了和当前模块有关的信息

    使用module.exports = {}即可向外暴露方法与变量

    语法糖是exports = {}

    如果同时使用了module.exports 和 exports 进行了暴漏，module.exports的优先级在exports之上，require接受的永远是modeule.exports暴漏的对象，不管暴漏的先后顺序

## npm与包

## 包
    Node.js中的第三方模块又叫做包。
    
## 包的来源
    包是由第三方提供的

## 为什么需要包
    包是基于内置模块封装出来的，提供了更高级、更方便的API，极大的提高了开发效率

## 全球最大的包共享平台
    https://www.npmjs.com/

## nrm 包镜像管理工具
    nrm ls 命令查看镜像地址
    nrm use 镜像地址 切换镜像地址

## 包的结构与规范
    包必须以单独的目录存在

    包的顶级目录下必须包含package.json这个包管理配置文件

    package.json中必须包含name，version，main这三个属性，分别代表包的名字、版本号、包的入口
    
    更多约束可以参考：https://yarnpkg.com/zh-Hans/docs/package-json

## 开发属于自己的包 （my-tools）
    初始化包的基础结构

        新建my-tools文件夹，作为包的根目录

        在my-tools文件夹中，新建如下三个文件：

            package.json (包管理配置文件)

                拥有属性：

                    name：包的名称

                    version： 包的版本号

                    main：包的入口文件

                    description：包的描述信息

                    keywords：搜索的关键字

                    license： 遵循的开源许可协议（npm希望默认ISC协议）

            index.js (包的入口文件)

                在文件中定义时间初始化的方法

            README.md (包的说明文档)

                通过markdown将包的使用方法说明清楚即可

## 将不同的功能进行模块化拆分 （my-tools）
    将不同的方法通过功能进行分类到不同的js文件下，通过module.exports进行暴露，在index入口文件中通过require进行引入然后再暴露出去

## 发布自己的包
    在终端中使用 npm login 登陆自己的账号

    注意：在登陆的时候npm的地址一定要是官方地址不能是淘宝镜像

    切换到包的文件夹下使用 npm publish 即可上传自己的包

    注意：上传前要注意报的名称不能重名，否则会失败

## 删除自己的包
    在终端上运行 npm unpublish packageName --force 即可删除自己的包

    注意：
        通过该命令只能删除72小时以内发布的包，过时将永远不能删除

        通过该命令删除的包在24小时以内不允许重复发布

        尽量不要发布没有意义的包

## 更新包
    通过 npm version ... 可以设置包的版本，有如图几个参数

![命令](./image.png)

    也可以直接使用 npm version xx.xx.xx 直接更新版本

    然后再通过npm publish 就可以更新包的版本

## 模块的加载机制
    模块会优先从缓存中加载：

        模块在第一次加载后会被缓存，这意味着多次调用require()不会导致模块的代码被执行多次
        
        注意：不论是内置模块、用户自定义模块、害死第三方模块，他们都会优先从缓存中加载，从而提高模块的加载效率

## 内置模块的加载机制
    内置模块的加载优先级是最高的，即使node_modules目录下有同名的包，require('fs') 始终返回内置的fs模块

## 自定义模块的加载机制
    必须有路径标识符 ./ 或 ../ 否则node会把它当作内置模块或者第三方模块

    如果导入时省略了扩展名 node 会以 js、json、ndoe 的顺序依次补全扩展名来进行加载

## 第三方模块的加载机制
    当nodeJS尝试从node_modules文件夹中查找第三方模块而没有找到的时候，会从当前文件的父目录开始逐次向上级目录查找node_modules下的模块，直到文件系统的根目录

## 目录作为模块
    如果在引入时使用目录作为模块，那么node会在目录下查找package.json文件，并寻找main属性，如果没有package.json或者main入口不存在或无法解析,node则会试图加载目录下的index.js文件，如果还是没有，那么就会报错

## Express框架
    中文官网：http://www.expressjs.com.cn

    Express 是基于Node.js平台，快速、开放、极简的web开发框架。

    Express是基于http模块封装的，是专门用来创建Web服务器的。

## 使用Express框架创建一个web服务器
### 引入express
```js
const express = require('express')
```

### 创建web服务器
```js
const app = express()
```

### 启动web服务器
```js
app.listen(8081,() => {
    console.log('express server running at http://127.0.0.1:8080')
})
```

### 监听get或者post方法，并处理参数
```js
app.get('/user',(req,res) => {
    console.log(req.query)
    res.send({name: 'wzh',age: 24,gender: '男'})
})

app.post('/user',(req,res) => {
    console.log(req.query)
    res.send("请求成功")
})
```

    req.query获取的是用户的传参,默认是空对象

### 获取动态参数
```js
app.get('/user/:id',(req,res) => {
    console.log(req.params)
    res.send(req.params)
})
```

    req.params默认是空对象

    id是一个动态参数，用户再调用接口的时候在接口名后拼接/value后就可以在req.params里面获取到一个与id键值对的对象,id是名称并不固定，：是固定的

## 托管静态资源
    express提供了 express.static()，通过它就可以方便的创建一个静态资源服务器
    
    例如，将public目录下的图片、css文件、JavaScript文件对外开放访问

```js
app.use(express.static('public'))
```

    如果要托管多个静态资源的目录，就多次调用就好了

    如果托管的文件夹内有同名文件，以先托管的为基准

    在访问托管的文件夹内的文件时，路径上不需要加托管的文件夹名，如果想要加上一个路径前缀的话，如下

```js
app.use('/public',express.static('public'))
```

## nodemon热加载开发工具

    安装：npm install -g nodemon 全局安装即可

    使用：再启动项目时把node index命令替换为 nodemon index即可

## express 路由
    express的路由是一个客户端请求与服务器处理函数之间的映射关系

    express中路由分3部分组成，分别是请求的类型，请求的URL地址，处理函数

    如：
```js
app.method(path,function(){}) //method(类型) path(url地址) function(函数)
```

## 路由的匹配过程

    每当有一个请求到达服务器之后，需要先经过路由的匹配，匹配成功后采后调用相应的处理函数。
    
    在匹配时，会按照路由的顺序进行匹配，如果请求类型和请求的URL同时匹配成功，在Express会将这次请求转交给对应的函数进行处理

    路由匹配的注意点：

        按照定义的先后顺序进行匹配

        请求类型和请求的URL必须同时匹配成功

## 路由的使用

### 最简单的用法

    直接挂在在app上

```js
const app = express()

app.get('/',(req,res) => {
    res.send("hello world")
})

app.post('/',(req,res) => {
    res.send("hello world")
})

app.listen(80,() => {
    console.log('express serve running at http://127.0.0.1')
})
```

## 模块化路由
    为了方便对路由进行模块化的管理，Express不建议将路由直接挂载到app上，而是推荐将路由抽离为单独的模块。

    1、创建路由模块对应的js文件
    
    2、调用express.Router()函数创建路由对象

```js
const express = require('express')

const router = express.Router()

```

    3、向路由对象上挂载具体的路由

```js
router.get('/list/user',(req,res) => {
    res.send('get 请求成功')
})

router.post('/list/add',(req,res) => {
    res.send('post 请求成功')
})
```

    4、使用module.exports向外共享路由对象

```js
module.exports = router
```

    5、使用app.use()函数注册路由模块

```js
const express = require('express'),
      router = require('./router/router'), 
      app = express()

app.use(router)

app.listen(80,() => {
    console.log("Express Server running at http://127.0.0.1")
})
```

    注意：app.use() 函数的作用，就是来注册全局中间件

## 为路由模块添加前缀

```js
app.use('/api',router) //访问路由需要前缀 如：/api/list/user
```

## 中间件的概念

    中间件是业务处理中的处理环节

## Express 中间件的调用流程
    当一个请求到达Express的服务器之后，可以连续调用多个中间件，从而对这次请求进行预处理

    流程： 客户端请求→中间件1→中间件2→中间件N→处理完毕响应这次请求→响应客户端

## Express 中间件的格式

    Express 的中间件，本质上就是一个function处理函数

    中间件函数的形参列表中，必须包含next参数，而路由处理函数中至半酣req和res

## next 函数的作用

    next函数是实现多个中间件连续调用的关键，他表示把流转关系转到下一个中间件或路由。

## 定义一个简单的中间件函数

```js
const express = require('express')

const app = express()

const mw = function(req,res,next){

    console("这是一个中间件函数")

    next() //放行
}
```

## 全局生效的中间件

    只需要调用app.use(mw)即可注册一个全局生效的中间件

    注册后任何一个请求都会先进入中间件

    如果注册中间件是给了一个路径的话，那么只有在url中有这个路径的请求会调用中间件

## 中间件的作用

    多个中间件之间，共享同一分req和res，基于这样的特性，我们可以在上游的中间件中，统一为req和res对象添加自定义的属性和方法，供下游的中间件或路由进行使用

## 局部生效的中间件
    不使用 app.use() 注册的中间件就是局部中间件

```js
const express = require('express')

const app = express()

const mw1 = function(req,res,next) {
    console.log("局部生效")
    next()
}

app.get('/',mw1,(req,res) => {//中间件会生效
    res.send("request success")
})

app.get('/user',(req,res) => {//中间件不会生效
    res.send("request success")
})

app.listen(80,() => {
    console.log("express server running at http://127.0.0.1")
})
```

## 定义多个局部生效的中间件

```js
const express = require('express')

const app = express()

const mw1 = function(req,res,next) {
    console.log("局部生效")
    next()
}

const mw2 = function(req,res,next) {
    console.log("局部生效2")
    next()
}

app.get('/',mw1,mw2,(req,res) => {//中间件会生效
    res.send("request success")
})
//或者
app.get('/',[mw1,mw2],(req,res) => {//中间件会生效
    res.send("request success")
})

app.listen(80,() => {
    console.log("express server running at http://127.0.0.1")
})
```

## 中间件的使用注意事项
    一定要在路由之前定义中间件
    
    客户端发送过来的请求，可以连续调用多个中间件进行处理

    执行完中间件的业务代码之后，不要忘记调用next()函数

    为了防止代码逻辑混乱，调用next()函数后不要再写额外的代码

    连续调用多个中间件时，多个中间件之间，共享req和res对象

## 中间件的分类
    Express官方把常见的中间件用法，分成5大类，分别是：

        1、应用级别的中间件

            通过app.use()或app.post()或app.get(),绑定到app实例上的中间件

        2、路由级别的中间件

            绑定到express.Router()实例上的中间件叫做路由级别的中间件

        3、错误级别的中间件

            专门用来捕获整个项目中发生的异常错误，从而防止项目异常崩溃的问题

            格式：必须由4个形参，形参顺序从前到后分别是(err,req,res,next)

            错误中间件一定放在所有路由的后面

```js
            const express = require('express'),
                app = express()

            app.get('/user',(req,res) => {
                //人为制造错误
                throw new Error("服务器内部错误")
                res.send("Home Page")
            })

            //定义错误级别的中间件，捕获整个项目的异常错误，从而防止程序的崩溃
            app.use((err,req,res,next) => {
                console.log('发生错误' + err.message)
                res.send('Error' + err.message)
            })

            app.listen(80,() => {
                console.log("express server running at http://127.0.0.1")
            })
```

        4、Express内置的中间件

            express 4.16.0 版本开始就内置了 3 个常用的中间件

            1、express.static 快速托管静态资源的中间件（无兼容性）

            2、express.json 解析JSON格式的请求体数据(有兼容性，尽在 4.16.0+ 版本可用)

```js
                //配置解析 application/json 格式数据的内置中间件
                app.use(express.json())
```

            3、express.urlencoded 解析URL-encoded 格式的请求体数据(有兼容性，尽在 4.16.0+ 版本可用)

```js
                //配置解析 application/x-www-form-urlencoded 格式的数据的内置中间件
                app.use(express.urlencoded({ extended: false }))
```

        5、第三方的中间件

            npm i 后 require引入然后时候app.use()注册即可

## 自定义模块
    例：模拟一个类似express.urlencoded的中间件，来解析post提交到服务器的表单数据

    1、定义中间件

    2、监听req的data事件
        
        监听data事件来获取客户端发送到服务器的数据，如果数据比较大无法一次发送完毕，客户端会把数据切割后分批发送，所以data事件可能会触发很多次，每一次触发所获取到的数据只是一部分，需要手动拼接

        通过
```js
            let str = ''
            req.on('data',(chunk) => {
                str += chunk
            })
```
        来监听data事件

    3、监听req的end事件

       当请求体数据接收完毕后，会自动触发end事件，一次可以在end事件中拿到并处理完整的请求体数据

    4、使用querystring模块解析请求体数据

        nodeJS内置了一个querystring模块，专门用来处理查询字符串，通过这个模块提供呃parse()，可以轻松把查询字符串解析成对象格式

```js
                const  querystring = require('querystring')
                
                //监听end事件拿到完整的请求体数据
                req.on('end',() => {
                    //处理完整的请求体数据，把字符串格式的请求体数据解析为对象格式
                    str = querystring.parse(str)
                })
```

    5、将解析出来的数据对象挂载为req.body