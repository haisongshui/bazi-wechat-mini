# 八字命理小助手-微信小程序前端

## 项目简介

八字命理小助手是一款基于微信小程序平台的命理分析工具，用户只需输入阳历出生日期和时辰，系统即可自动计算对应的农历日期、天干地支、五行属性、五行缺失情况及生肖信息。

## 技术栈

- 微信小程序原生开发
- 采用原生JS，未使用第三方框架
- 通过API与后端交互，获取八字计算结果

## 环境配置

项目支持两个环境：
- 开发环境（本地）：`http://localhost:8080/api`
- 生产环境（线上）：`https://api.your-domain.com/api`

### 微信小程序配置

在使用前，需要在 `project.config.json` 文件中配置你自己的微信小程序 appid：

```json
{
  "appid": "YOUR_WECHAT_APPID",
  "compileType": "miniprogram",
  ...
}
```

你可以在[微信公众平台](https://mp.weixin.qq.com/)注册并获取 appid。

### 切换环境

在 `config/api.js` 文件中，修改 `CURRENT_ENV` 变量：
- 本地开发：`const CURRENT_ENV = ENV.DEV;`
- 线上环境：`const CURRENT_ENV = ENV.PROD;`

## 安全域名配置

为了让微信小程序能够正常访问后端API，需要在微信公众平台进行域名配置：

1. 登录[微信公众平台](https://mp.weixin.qq.com/)
2. 进入"开发管理" > "开发设置" > "服务器域名"
3. 在"request合法域名"中添加：
   - 开发环境：`localhost:8080`（仅在开发工具的本地模式下有效）
   - 生产环境：`api.your-domain.com`

**注意：** 
- 微信小程序正式环境只支持HTTPS请求，已配置为使用HTTPS
- 在开发者工具中，可以勾选"不校验合法域名..."选项进行本地测试

## 目录结构

```
bazi-frontend/
├── config/             # 配置文件
│   └── api.js          # API接口配置
├── pages/              # 页面文件
│   ├── index/          # 首页
│   ├── input/          # 信息输入页
│   └── result/         # 结果展示页
├── static/             # 静态资源
│   └── images/         # 图片资源
├── utils/              # 工具函数
│   ├── baziService.js  # 八字服务
│   └── request.js      # 网络请求封装
├── app.js              # 小程序入口文件
├── app.json            # 小程序配置文件
├── app.wxss            # 全局样式
└── sitemap.json        # 微信索引配置
```

## 开发和运行

1. 安装微信开发者工具
2. 导入项目目录
3. 确保后端服务已启动（默认地址：http://localhost:8080/api）
4. 在开发者工具中编译预览

## 页面说明

- 首页：展示小程序简介和进入按钮
- 信息输入页：提供阳历日期和时辰选择
- 结果展示页：展示八字计算结果，包含农历日期、天干地支、五行属性等信息

## API接口

- `/bazi/calculate`：八字计算接口，传入阳历日期和时辰，返回计算结果 