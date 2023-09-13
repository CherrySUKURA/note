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
