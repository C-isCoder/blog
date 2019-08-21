+++
author = "Xiaodan.C"
categories = ["API"]
date = "2019-08-20"
description = "医邦人 OCR 接口文档"
featured = "pic02.jpg"
featuredalt = "Pic 2"
featuredpath = "date"
linktitle = ""
title = "医邦人证件识别接口说明文档"
type = "post"
+++

## 营业执照识别 `../ocr/license`

#### 请求参数

> form-data 表单请求

1. `file` 文件

2. `imageUrl` 文件链接

#### 返回参数

```json
{"code":0,"msg":"success","data":{"registerId":"注册号","corporation":"法人","address":"注册地址","companyName":"公司名称","operatingPeriod":"营业期限","businessScope":"经营范围"}}
```

## 手写体识别 `../ocr/write`

#### 请求参数

> form-data 表单请求

1. `file` 文件

2. `imageUrl` 文件链接

#### 返回参数

```json
{"code":0,"msg":"OK","data":{"sessionId":"","items":[{"itemString":"本","ItemCoord":{"x":1663,"y":934,"width":359,"height":572},"itemConf":0.8426098227500916,"words":[{"character":"本","confidence":0.8426098227500916}]}]}}
```

## 通用识别 `../ocr/general`

#### 请求参数

> form-data 表单请求

1. `file` 文件
2. `imageUrl` 文件链接

#### 返回参数

```json
{"code":0,"msg":"success","data":{"language":"zh","requestId":"42c36882-35df-41cf-ab4d-05309d51167b","textDetections":[{"detectedText":"丛晓丹","confidence":99,"polygon":[{"x":25,"y":10},{"x":101,"y":10},{"x":101,"y":47},{"x":25,"y":47}],"advancedInfo":"{\"Parag\":{\"ParagNo\":1}}"}]}}
```

## 开票信息识别 `../ocr/invoice`

#### 请求参数

> form-data 表单请求

1. `file` 文件

2. `imageUrl` 文件链接

#### 返回参数

```json
{"code":0,"msg":"success","data":{"companyName":"公司名称","companyAddress":"公司地址","bankName":"开户行","bankAccount":"银行汇款账号","taxCode":"纳税人识别号","zipCode":"邮编","telephone":"电话","depotAddress":"仓库地址"}}
```

## 身份证识别 `../ocr/identity`

#### 请求参数

> form-data 表单请求

1. `file` 文件

2. `imageUrl` 文件链接

#### 返回参数

```json
{"code":0,"msg":"success","data":{"requestId":"11bf6e0d-21fe-4c21-98bd-1d32159d269e","name":"证件姓名","sex":"性别","nation":"民族","birth":"出生日期","address":"地址","idNum":"身份证号","validDate":"证件的有效期","authority":"发证机关"}}
```

## 银行卡识别 `../ocr/bank`

#### 请求参数

> form-data 表单请求

1. `file` 文件

2. `imageUrl` 文件链接

#### 返回参数

```json
{"code":0,"msg":"OK","data":{"bankCardCode":"卡号","bankCardType":"卡类型","bankCardName":"卡名字","bankInfo":"银行信息","validityDate":"有效期"}}
```

## 收货授权委托书识别 `../ocr/consignee`

#### 请求参数

> form-data 表单请求

1. `file` 文件

2. `imageUrl` 文件链接

#### 返回参数

```json
{"code":0,"msg":"success","data":{"companyName":"公司名","employeeName":"被授权人名","employeeId":"被授权人身份证","employeePhone":"被授权人电话","timeLimit":"期限","address":"收货地址"}}
```

## 采购授权委托书识别 `../ocr/purchase`

#### 请求参数

> form-data 表单请求

1. `file` 文件

2. `imageUrl` 文件链接

#### 返回参数

```json
{"code":0,"msg":"success","data":{"companyName":"公司名","employeeName":"被授权采购人","employeeId":"被授权采购人身份证","employeePhone":"被授权采购人电话","timeLimit":"期限"}}
```

## 采购及收货委托书识别 `../ocr/consignee`

#### 请求参数

> form-data 表单请求

1. `file` 文件

2. `imageUrl` 文件链接

#### 返回参数

```json
{"code":0,"msg":"success","data":{"companyName":"公司名","employeeName":"被授权采购及收货人名","employeeId":"被授权采购及收货人身份证","employeePhone":"被授权采购及收货人电话","timeLimit":"期限","address":"收货地址"}}
```

[GitHub 链接🔗cloud-ocr](https://github.com/C-isCoder/cloud-ocr)

---