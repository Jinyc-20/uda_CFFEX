# 文本分类模型

作者：支龙

2020年9月

## 项目说明

通过**HTTP POST**方式发送参数，本服务将提取文本中各类实体信息并返回结果

以下模块可独立调用

**cffex_uda**    

## 微服务：文本分类（主题分类，违规类别分类等）

### 服务url `xxx.xx.xx.xx:xxxx/predict`

### 请求方式 `POST`

### 请求参数：JSON格式

| 参数    | 类型   | 是否必选 | 描述             | 默认值 |
| ------- | ------ | -------- | ---------------- | ------ |
| uuid    | string | 否       | 文档的唯一标志码 | 无     |
| content | string | 是       | 文档内容         | 无     |

请求示例

```
{
"uuid": "4596707759",
"content": "2月CPI公布：同比上涨1.5%  看看你买啥贵了，买啥便宜了？】国家统计局今天公布的数据显示：2月全国居民消费价格指数CPI同比上涨1.5%，涨幅比上月回落0.2个百分点。其中，食品价格同比涨幅回落是影响CPI走势的核心因素。从单项食品看，羊肉、牛肉价格涨幅居前，鲜果和鲜菜价格小幅波动，而鸡蛋、猪肉和水产品价格却处在下行通道， 涨跌互抵，使得食品价格平稳运行 。在非食品中，医疗保健、教育文化和娱乐、居住价格依旧领涨，但涨幅平稳。国研中心宏观经济研究部研究员张立群表示：总体来看，价格还是总体平稳，或者是一个走低基本趋势。（记者 柴华 武立丰 张宏斌",
}
```



### 返回字段：JSON格式

| 字段         | 说明                          |
| ------------ | ----------------------------- |
| status       | 状态码                        |
| message      | 连接状态                      |
| result.probabilities    | 预测为各类别的概率              |
| result.label | 最终的预测标签 |

返回示例

```
{
    "status": 200,
    "message": "OK",
    "result": {
        "probabilities": array([0.01, 0.99]),
        "label": B
    }
}
```

### 状态码说明：
```
200：连接正常
405：请求方法错误，仅支持post请求
```