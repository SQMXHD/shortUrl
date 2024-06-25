# 不用数据库的短网址V2.0

#### 项目介绍
> 未使用数据库，利用php的数组保存数据，可以放二级文件夹使用   
> 生成二维码为jquery.qrcode.js   
> 生成短网址的形式：默认是5位小写字母和数字，可选从1开始依次增加的数字
> 仅供个人学习只用, 不适用大批量商用      
> <mark>***后台登录密码请一定要修改成自己的***<mark>    

#### V2.1更新
增加一个简单的后台管理   /admin.php
修复部分已知的bug
php8的支持

#### 使用说明
0. 将所有文件复制到你的项目中。
1. urls123.php和urlsabc.php文件需设置为777权限
2. 修改config.php

```html
'title' => "短网址演示",                       //网站标题
'site' => "https://51015.cn/demo/shortUrl",  //短网址域名
//不允许缩短的域名，单个匹配，*表示所有的二级域名
'blackList' => array('*.51015.cn','baidu1.com','youku1.com'),
'key' => "idjl",                             //token 使用的密钥

//根据需求修改
'use_rewrite' => 1,                          // 是否使用伪静态,默认使用
//生成的短网址类型：abc表示字母数字混合，123为纯数字累加方式
'type' => 'abc',


// 管理后台登录账号和密码, 请一定要修改成自己的
'adminUser' => 'admin',
'adminPWD' => 'aB12345!',
```

3. 访问你设置的短网址域名/index.php
4. 如果你使用了这套代码，请给本项目点个Star

#### 演示地址
https://51015.cn/demo/shortUrl/index.php     


#### 伪静态的使用
默认开启伪静态，可以关闭，config.php中修改'use_rewrite' => 2即可。   
apache可以直接使用；    
nginx需要配置文件中引入.htaccess-nginx     

nignx引入教程：https://jianlong.blog.csdn.net/article/details/85689930

```html
if (!-e $request_filename) {
#-e filename 如果 filename存在，则为真
#-d filename 如果 filename为目录，则为真 
#-f filename 如果 filename为常规文件，则为真
#-L filename 如果 filename为符号链接，则为真
#-r filename 如果 filename可读，则为真 
#-w filename 如果 filename可写，则为真 
#-x filename 如果 filename可执行，则为真
#-s filename 如果文件长度不为0，则为真
#-h filename 如果文件是软链接，则为
rewrite /([^/.]+)/?$  /url/create.php?id=$1 last;
#例：https://qq.com/url/
#rewrite /([^/.]+)/?$  /url/create.php?id=$1 last;
#https://qq.com/短地址
}
```

