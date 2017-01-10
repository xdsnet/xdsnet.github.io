# ucloud静态wiki、blog小站的建立

[toc]
## ucloud个人站的开通

1. 开通[ucloud](www.ucloud.cn)的账号，具体过程这里不再累述，请参见网上其他文章后文假定有`auser`用户是ucloud上有效用户
2. 在`auser`用户下建立一个单地域的对象存储空间。比如 `（XYZ.cn-bj.ufileos.com）`。则该空间即同步开通一个域名（网址）`XYZ.cn-bj.ufileos.com`的静态页面网站，所有在该存储空间的内容均可以以`XYZ.cn-bj.ufileos.com`的下的文件对象（包含子目录路径文件信息）如`path/afile.html`均可以直接以`http://XYZ.cn-bj.ufileos.com/path/afile.html`来访问到。
3. 至此，基本的Ucloud个人站其实已经建立完成。

## ucloud个人站文件的上传

1. 新的`XYZ.cn-bj.ufileos.com`现在肯定什么内容都没有的，你需要上传文件；
2. 上传文件需要[https://console.ucloud.cn/ufile/tools](https://console.ucloud.cn/ufile/tools)里面的*文件管理*工具，你根据系统下载对应版本即可；
3. 上传文件需要配置`config.cfg`文件，填入你的`public_key` 和 `private_key`实际值，该内容在`ucloud`管理页面的`控制台>监控管理>API密钥`中可以查到。
4. 采用`<filemgr-命令行工具> --action sync --bucket <存储空间名>  --dir <需上传文件目录>`即可同步上传（下次再执行则只会传递更新），这里
  - `filemgr-命令行工具`需要换成你实际选择的工具版本全名，比如我选用的是`filemgr-linux64`
  - `存储空间名`需要换成你选择的存储空间名，比如前面`XYZ.cn-bj.ufileos.com`对应的存储空间是`XYZ`
  - `需上传文件目录`也需要根据你实际定义

*注意*ucloud的对象存储其实已经没有了常规意义上的目录的概念了，目录路径信息已经成为文件对象的一些描述属性了，这里体现在文件的引用名上，即其URI地址中除了前面的`XYZ.cn-bj.ufileos.com`部分是代表着存储空间的基本地址，后面的无论多少个目录符号其实是无意义的。

## 利用wiki-in-box搭建纯静态支持`markdown`页面站点

   参考我的另外一篇博文[github静态wiki、blog的建立](杂谈:github静态wiki、blog的建立)

------
## 参考
* [http://www.cnblogs.com/sosoft/p/3456631.html](http://www.cnblogs.com/sosoft/p/3456631.html) 改写规则式定义
* [http://www.w3school.com.cn/jsref/jsref_obj_regexp.asp](http://www.w3school.com.cn/jsref/jsref_obj_regexp.asp)了解`JavaScript`规则式
* [http://www.uoota.com/blog/archives/12217?geek](http://www.uoota.com/blog/archives/12217?geek)了解ucloud静态网站建立规则

