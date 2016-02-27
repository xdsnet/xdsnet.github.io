# github静态wiki、blog小站的建立
[toc]
## github个人站的开通
1. 开通[github.com](www.github.com)的账号，具体过程这里不再累述，请参见网上其他文章后文假定有`auser`用户是github上有效用户
2. 在`auser`用户下建立一个名为`auser.github.io`的仓库，即`（https://github.com/auser/auser.github.io）`。则该仓库即同步开通一个域名（网址）`auser.github.io`的静态页面网站，所有在仓库`auser.github.io`的`master`分支下的文件（包含子目录路径文件）如`path/afile.html`均可以直接以`http://auser.github.io/path/afile.html`来访问到。
3. 至此，基本的github个人站其实已经建立完成。

对于个人其他项目仓库（例如项目仓库`https://github.com/auser/brep`），其实在`auser.github.io`建立起来后，则自动会有一个名为`auser.github.io/brep/`的静态页面地址指向该项目仓库，以完成项目说明，不过因为`brep`项目仓库这时`master`分支会放置该项目相关的文件，而不会用来放置静态`html`页面，所以github会让`auser.github.io/brep/`对应`https://github.com/auser/brep/tree/gh-pages/`。

## 利用wiki-in-box搭建纯静态支持`markdown`页面站点
因为github提供的站点服务是纯静态web页面服务，所以比较不方便，特别是需要专门写`HTML`代码是很繁琐的事情。我就选择了利用[wiki-in-box](http://dmscode.github.io/Wiki-in-box/)搭建纯静态支持`markdown`的wiki、blog站点。

搭建过程十分简单，对于`auser.github.io`仓库，在`master`分支根目录下放置`wiki-in-box`的所有文件，即可，所有`markdown`文件都放置在`data`子目录下，相关图片放置在`imgs`子目录下。具体`wiki-in-box`的使用参见其项目主页。

如果是其他项目的页面则放置在`gh-pages`分支下即可。

**注意**:所有的`markdown`文件需要以`.md`作为扩展名，但在写链接时都不带`.md`的扩展名，即对文件`/data/path/file.md`，在链接中需要写为`(path:file)`不能带有`.md`扩展名，否则链接会出错。

这里补充一点`wiki-in-box`的`markdown`编写链接时对中文名文件和路径问题的处理：
* 原由：含中文的路径或文件名，不能按`wiki-in-box`介绍中的方式给出链接，~~这是因为项目中的`marked.js`文件对中文链接支持的瑕疵~~。这是因为`index.html`中一个规则式定义中没有包括对中文字符、标点等的检测。

* ~~临时处理：~~
    1. ~~在路径或文件名中避免出现中文（其实是所有非英语字符），这个我个人不是太推荐，但也是一种可行的方案~~
    2. ~~我找到的一种临时处理方法，对包含中文的链接，改写链接提供语法为 `[链接文字](./index.html?name=含中文的路径)`，例如按`wiki-in-box`介绍的标准一个文章链接为`[文章abc](路径:文件名)`，因为含中文不能正确处理，可改成`[文章abc](./index.html?name=路径:文件名)`即可正常链接，不过这样的处理方法有一个附加的特性就是会打开新的窗口来浏览，而标准的模式会在当前窗口导航到新的链接。~~
    
较正式的处理是修改该处规则式定义。把
```javascript
var reg = new RegExp("^[\\w\\-\\:]+$");	// 验证命名域
```
改为
```javascript
var reg = new RegExp("^[\.\\w\\-\\:\u2E80-\u2FDF\u2FF0-\u2FFF\u3000-\u303F\u31C0-\u31EF\uFE00-\uFFEF\u4E00-\u9FA5]+$");	// 验证命名域
```
**注意**在这个规则式中我还包含了`.`，因为当前目录和文件命名中都可以额外的包含它，而不仅仅是扩展名的分隔啦。这个问题的修复已经提交给了`wiki-in-box`，期待他的修复，这个规则式应该还能改写以支持所有非英语文件命名，因为我没有这样的需要，所以先就改成这样啦。

------
### 参考
* [http://www.cnblogs.com/sosoft/p/3456631.html](http://www.cnblogs.com/sosoft/p/3456631.html) 改写规则式定义
* [http://www.w3school.com.cn/jsref/jsref_obj_regexp.asp](http://www.w3school.com.cn/jsref/jsref_obj_regexp.asp)了解`JavaScript`规则式
* [https://help.github.com/categories/github-pages-basics/](https://help.github.com/categories/github-pages-basics/)了解github静态网站建立规则

