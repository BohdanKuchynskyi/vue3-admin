Vue3 Admin


## Installation and use


 > Environment requirements: The version requires Node 14.18+ / 16+ and above. Node 12 / 13 / 15 is no longer supported.
 > It is recommended to use pnpm. If you use yarn, please use Yarn1.x version, otherwise the dependencies may not be installed.

  
- Get the project code

```bash
git clone https://github.com/jeecgboot/jeecgboot-vue3.git
```

- Installation dependencies

```bash
cd jeecgboot-vue3

pnpm install
```

- 配置接口地址 `.env.development`

```bash
VITE_PROXY = [["/jeecgboot","http://localhost:8080/jeecg-boot"],["/upload","http://localhost:3300/upload"]]
VITE_GLOB_DOMAIN_URL=http://localhost:8080/jeecg-boot
```

> 说明：把`http://localhost:8080/jeecg-boot` 换成自己地址，其他不用改。


- run

```bash
pnpm serve
```


- build

```bash
pnpm build
```


## Docker镜像启动前端(单体模式)

- host设置

>注意： 需要把`127.0.0.1`替换成真实IP 比如`192.`开头,不然后端不通。

```bash
127.0.0.1 jeecg-boot-system
127.0.0.1 jeecg-boot-gateway
```


- 下载项目

```bash
git clone https://github.com/jeecgboot/jeecgboot-vue3.git

cd jeecgboot-vue3
```

- 配置接口域名 `.env.production`

```bash
VITE_GLOB_API_URL=/jeecgboot
VITE_GLOB_DOMAIN_URL=http://jeecg-boot-system:8080/jeecg-boot
```
后台单体启动 [见此文档](https://help.jeecg.com/java/setup/docker/up.html)

- 编译项目

```bash
pnpm install

pnpm build
```

- 启动容器
```bash
docker build -t jeecgboot-vue3 .
docker run --name jeecgboot-vue3-nginx -p 80:80 -d jeecgboot-vue3
```

- 访问前台

http://localhost

## Docker镜像启动前端(微服务模式)
> 这里只写与单体的区别步骤

-  区别1. 修改后台域名
.env.production

```bash
VITE_GLOB_API_URL=/jeecgboot
VITE_GLOB_DOMAIN_URL=http://jeecg-boot-gateway:9999
```

后台微服务启动 [见此文档](https://help.jeecg.com/java/springcloud/docker.html)

- 区别2. 修改Dockerfile文件

```bash
- 把`http://jeecg-boot-system:8080/jeecg-boot`替换成 `http://jeecg-boot-gateway:9999`
- 把`jeecg-boot-system`替换成 `jeecg-boot-gateway`
```

-  其他与单体模式一样

```bash
镜像需要重现构建，最好把单体的镜像删掉，重新构建docker镜像。
```







## 入门必备

本项目需要一定前端基础知识，请确保掌握 Vue 的基础知识，以便能处理一些常见的问题。 建议在开发前先学一下以下内容，提前了解和学习这些知识，会对项目理解非常有帮助:

*   [JeecgBoot-Vue3文档](http://help.jeecg.com)
*   [Vue3 文档](https://cn.vuejs.org/)
*   [Vben文档](https://doc.vvbin.cn)
*   [Ant-Design-Vue](https://www.antdv.com/docs/vue/introduce-cn/)
*   [TypeScript](https://www.typescriptlang.org/)
*   [Vue-router](https://router.vuejs.org/zh)
*   [Es6](https://es6.ruanyifeng.com/)
*   [Vitejs](https://cn.vitejs.dev/guide/)
*   [Pinia(vuex替代方案)](https://pinia.esm.dev/introduction.html)
*   [Vue-RFCS](https://github.com/vuejs/rfcs)
*   [Vue2 迁移到 3](https://v3.vuejs.org/guide/migration/introduction.html)
*   [vxetable文档](https://vxetable.cn)
*   [~~WindiCss~~](https://windicss.netlify.app/)


##   浏览器支持

**本地开发**推荐使用`Chrome 最新版`浏览器，**不支持**`Chrome 90`以下版本。

**生产环境**支持现代浏览器，不支持 IE。

| [![IE](https://raw.githubusercontent.com/alrra/browser-logos/master/src/archive/internet-explorer_9-11/internet-explorer_9-11_48x48.png)](http://godban.github.io/browsers-support-badges/)IE | [![ Edge](https://raw.githubusercontent.com/alrra/browser-logos/master/src/edge/edge_48x48.png)](http://godban.github.io/browsers-support-badges/)Edge | [![Firefox](https://raw.githubusercontent.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png)](http://godban.github.io/browsers-support-badges/)Firefox | [![Chrome](https://raw.githubusercontent.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png)](http://godban.github.io/browsers-support-badges/)Chrome | [![Safari](https://raw.githubusercontent.com/alrra/browser-logos/master/src/safari/safari_48x48.png)](http://godban.github.io/browsers-support-badges/)Safari |
| --- | --- | --- | --- | --- |
| not support | last 2 versions | last 2 versions | last 2 versions | last 2 versions |

简版流程设计

![](https://oscimg.oschina.net/oscnet/up-1dc0d052149ec675f3e4fad632b82b48add.png)

![](https://oscimg.oschina.net/oscnet/up-de31bc2f9d9b8332c554b0954cc73d79593.png)

![](https://oscimg.oschina.net/oscnet/up-7f83b25159663686d67ed080eb16068c3b4.png)

仪表盘设计器
![](https://oscimg.oschina.net/oscnet/up-9c9d41288c31398d76b390bdd400f13a582.png)

![](https://oscimg.oschina.net/oscnet/up-fad98d42b2cf92f92a903c9cff7579f18ec.png)

报表设计器
![](https://oscimg.oschina.net/oscnet/up-64648de000851f15f6c7b9573d107ebb5f8.png)

![](https://oscimg.oschina.net/oscnet/up-fa52b44445db281c51d3f267dce7450d21b.gif)

![](https://oscimg.oschina.net/oscnet/up-68a19149d640f1646c8ed89ed4375e3326c.png)

![](https://oscimg.oschina.net/oscnet/up-f7e9cb2e3740f2d19ff63b40ec2dd554f96.png)

表单设计器
![](https://oscimg.oschina.net/oscnet/up-5f8cb657615714b02190b355e59f60c5937.png)

![](https://oscimg.oschina.net/oscnet/up-d9659b2f324e33218476ec98c9b400e6508.png)

![](https://oscimg.oschina.net/oscnet/up-4868615395272d3206dbb960ade02dbc291.png)

大屏设计器
![](https://oscimg.oschina.net/oscnet/up-402a6034124474bfef8dfc5b4b2bac1ce5c.png)

![](https://oscimg.oschina.net/oscnet/up-6f7ba2e2ebbeea0d203db8d69fd87644c9f.png)

![](https://oscimg.oschina.net/oscnet/up-ee8d34f318da466b8a6070a6e3111d12ce7.png)

![](https://oscimg.oschina.net/oscnet/up-6b81781b43086819049c4421206810667c5.png)


报表效果

![](https://static.oschina.net/uploads/img/201904/14160828_pkFr.png "")

![](https://static.oschina.net/uploads/img/201904/14160834_Lo23.png "")

![](https://static.oschina.net/uploads/img/201904/14160842_QK7B.png "")

![](https://static.oschina.net/uploads/img/201904/14160849_GBm5.png "")

![](https://static.oschina.net/uploads/img/201904/14160858_6RAM.png "")

接口文档

![](https://oscimg.oschina.net/oscnet/up-e6ea09dbaa01b8458c2e23614077ba9507f.png)


手机端
![](https://oscimg.oschina.net/oscnet/da543c5d0d57baab0cecaa4670c8b68c521.jpg)
![](https://oscimg.oschina.net/oscnet/fda4bd82cab9d682de1c1fbf2060bf14fa6.jpg)

PAD端
![](https://oscimg.oschina.net/oscnet/e90fef970a8c33790ab03ffd6c4c7cec225.jpg)
![](https://oscimg.oschina.net/oscnet/d78218803a9e856a0aa82b45efc49849a0c.jpg)
![](https://oscimg.oschina.net/oscnet/59c23b230f52384e588ee16309b44fa20de.jpg)



