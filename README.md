# 勾勾：一个基于谷歌的搜索工具

## 是什么

「勾勾」是一个搜索工具，搜索结果基于[谷歌](https://google.com)，致力于「安全和简洁」的搜索体验。

### 安全

- 「勾勾」是一个在`用户`与`谷歌`之间的代理，谷歌无法得知用户的隐私（如UserAgent、Cookie等），也无法`跟踪用户的结果点击`

- 部署简单，基于`JDK 11`，仅需一台处于`可以访问谷歌的网络`的主机即可

### 简洁

- ~~精简~~（丑陋）到极致的Web前端
- 提供Web API，轻松地自定义搜索前端（正在开发`基于命令行的搜索前端`）

## 如何使用

> 本程序通过`网页`和`Web API`两种方式提供服务。

### 网页

1)URL: https://176.122.157.73:5000

### API

#### 搜索

```bash
$ curl -X GET -k "https://176.122.157.73:5000/api/search?q=github&p=1"
{
  "key": "github",
  "page": 1,
  "amount": 223000000,
  "elapsed": 0.43,
  "entries": [
    {
      "name": "The world's leading software development platform · GitHub",
      "url": "https://github.com/",
      "desc": "GitHub brings together the world's largest community of developers to discover, share, and build better software. From open source projects to private team ..."
    }
  ],
  "error": null
}
```

#### 关键词提示

```bash
$ curl -X GET -k "https://176.122.157.73:5000/api/complete?q=github"
{
  "key": "github",
  "lints": [
    "github",
    "github<b> desktop</b>",
    "github<b> stock</b>",
    "github<b> microsoft</b>",
    "github<b> pages</b>",
    "github<b> api</b>",
    "github<b> tutorial</b>",
    "github<b> login</b>",
    "github<b> markdown</b>",
    "github<b> gist</b>"
  ],
  "error": null
}
```

## 开发计划

- 后端实现细节文档
- 基于命令行的搜索前端
- 可配置的缓存：内存与Redis

## 框架

> 站在巨人的肩膀上

- [Netty](https://netty.io/)
- [Jsoup](https://jsoup.org/)
- [SpringBoot](https://github.com/spring-projects/spring-boot)