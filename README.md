# dbblog_comment
dbblog评论仓库，使用gitalk插件 https://github.com/gitalk/gitalk/blob/master/readme-cn.md

## 原理
Gitalk 是一个利用 Github API,基于 Github issue 和 Preact 开发的评论插件，在 gitalk 的评论框进行评论时，其实就是在对应的 issue 上提问题。

## 安装教程
1. 引入js和css
```html
<link rel="stylesheet" href="https://unpkg.com/gitalk/dist/gitalk.css">
<script src="https://unpkg.com/gitalk/dist/gitalk.min.js"></script>
```


2. 添加一个容器：
```html
<div id="gitalk-container"></div>
```

3. 用下面的 Javascript 代码来生成 gitalk 插件：
```javascript
var gitalk = new Gitalk({
  clientID: 'GitHub Application Client ID',
  clientSecret: 'GitHub Application Client Secret',
  repo: 'GitHub repo',
  owner: 'GitHub repo owner',
  admin: ['GitHub repo owner and collaborators, only these guys can initialize github issues'],
  id: location.pathname,      // Ensure uniqueness and length less than 50
  distractionFreeMode: false  // Facebook-like distraction free mode
})

gitalk.render('gitalk-container')
```
其中的参数获取如下：
clientID 和 clientSecret 需要申请 GitHub Application，如果没有 [点击这里申请](https://github.com/settings/applications/new)，实例填写的域名是插件页面的域名。
示例如下：

![image.png](http://oss.dblearn.cn/dbblog/20190720/0799661323f4470e94354bf90531e0ac.png)

repo参数需要你新建一个仓库，作为评论容器

owner和admin都是你的github账号

## 演示
评论插件展示如下（[点击此处查看](http://www.dblearn.cn/article/1)）：
![image.png](http://oss.dblearn.cn/dbblog/20190720/a0f49334beaf4b55a18e935277ac9c7b.png)

## 注意事项
当你用 github 帐号登录（管理员）时，第一次加载会比较慢，因为第一次加载会自动在你 repo 的仓库下创建对应 issue。

因此，你需要在每篇文章发表后都点进去开启评论（创建issue），此处应该可以后端解决一下 // TODO

另外，参数里的id长度不能大于50，否则会创建issue失败



