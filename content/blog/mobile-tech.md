+++
author = "Xiaodan.C"
categories = ["mobile", "dev"]
date = "2019-08-20"
description = "手机端开发方案"
featured = "pic03.jpg"
featuredalt = "Pic 3"
featuredpath = "date"
linktitle = ""
title = "手机端开发方案"
type = "post"
+++

## UI

1. iOS、Android 都采用腾讯 QMUI 团队开源的 QMUI 控件。

2. 补充定制 QMUI 缺失控件，如 分享等。


## 基础组件

1. 开发语言 换成 Kotlin。

2. 使用 Kotlin 分装的 kit 包，其中包含 网络请求、工具类、控件、实用的扩展方法等。

3. MVP 模式开发，高度统一的开发模版。

4. 工具库的完善、丰富。

5. 本地存储 MMKV（微信开源）

6. 日志系统 Logan（美团开源）

7. [jetpack](https://developer.android.com/jetpack)

## 开发流程

1. 开发 -> 代码提交 -> 自动构建 -> 通知测试 -> 测试反馈 -> CodeReview 

2. 开发 -> 代码提交 -> CodeReview -> 自动构建 -> 通知测试 -> 测试反馈


## 技术栈

* 未来趋势，Kotlin 原生开发、Flutter 3端开发。

* Java、Kotlin、Dart、Python、Golang。


## 基础技术架构

* 网络相关：Retrofit、Gson

* 编程语言：Java、Kotlin

* 异步编程：RxAndroid、RxJava

* 代码组织：MVP

* 图片相关：Glide

* 基础相关：ktx、anko

---