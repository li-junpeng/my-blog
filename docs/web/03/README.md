## 搭建monaco-editor官网

这几天我的[DB兔](https://github.com/li-junpeng/dbtu-client)项目中，
需要使用到[monaco-editor](https://github.com/microsoft/monaco-editor)，
但是在查阅文档时遇到了难题，monaco-editor的[官网](https://microsoft.github.io/monaco-editor/)
访问速度非常慢（用了科学上网也是慢的很)
既然monaco-editor仓库提供了website，那么就自己在本地搭建一个，访问速度杠杠的。

下面是编译monaco-editor website的过程，编译需要用到webpack和yarn，如果自己本地有这些环境，就可以直接忽略了。

1. 安装webpack

```bash
npm install -g wepback
```

2. 安装yarn

```bash
npm install -g yarn
```

3. 将monaco-editor仓库代码克隆到本地
4. 在项目根目录运行`yarn intall`
5. 在项目根目录运行`yarn run build-monaco-editor`
6. 进入到website目录，然后运行`yarn run build`
7. 现在就可以使用命令`yarn run dev`运行website了
8. 使用命令`yarn run build-webpack`将项目打包，然后将dist放到web服务器中就可以运行了。
