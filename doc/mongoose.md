# mongooose使用

## 1.安装

创建node.js,安装mongoose:npm install mongoose

要求安装并打开了mongodb数据库服务器

## 2.使用流程

1）引入mongoose：

const mongoose = require('mongoose');

2）连接数据库：

mongoose.connect('mongodb://localhost/test');

其中test是数据库名

3）创建schema

const schema={

​	name:String,

​    age:Number,

​     health:String	

}

创建的schema在创建model时引用才有作用：mongoose.model('Cat',schema)

mongoose有自己的基本数据类型定义：

![image-20211124161600620](image-20211124161600620.png)

创建schema生效后，存储到数据库的数据必须遵守，否则不能存储，但系统没有原生的错误提示，只是存储一个空数据

4）创建model

const Cat = mongoose.model('Cat', { name: String });

5)写入数据库

const kitty = new Cat({ name: 'Zildjian' });

kitty.save().then(() => console.log('meow'));

写入后数据集的名称：是定义model的第一个参数，并且进行了修改，保证是英文的复数形式，如果没有s自动加s，不区分大小写，默认小写。

6）数据查找

数据集.find({查询条件}，callback(err,查询结果)=>{})

查询结果是一个Array，data[0]._doc是查询出的文档。



