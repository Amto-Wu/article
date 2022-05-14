hexo初级使用

本地搭建

```shell
# 安装hexo
npm install hexo-cli -g
# 初始化博客文件夹
hexo init blog
# 进入博客文件夹
cd blog
# 启动
hexo server
```



生成目录含义

- node_modules: 依赖包
- public：存放生成的页面
- scaffolds：生成文章的一些模板
- source：用来存放你的文章
- themes：主题
- ** _config.yml: 博客的配置文件**





命令汇总

```sh
# 安装hexo
npm install hexo-cli -g
# 初始化博客文件夹
hexo init blog
# 启动
hexo server
# 每次内容更改后，清理残留
hexo clean
# 重新生成内容
hexo generate
# 本地启动hexo
hexo server
```

