---
tags:
  - AI
  - wechat
  - Dify
share: "true"
categories:
  - tech
  - ai
title: Dify接入微信
date: 2024-07-16
---


###  需求前瞻

1. Dify如何把普通聊天机器人接入微信
2. 自定义编排工作流机器人如何联网搜索
3. 搜索获取的数据如何展示
### Dify接入

github项目地址 [dify-on-wechat](https://github.com/hanfangyuan4396/dify-on-wechat)
### 自定义Dify工具: Serper API

Dify没有直接提供SerperAPI的工具, 于是对着给的例子写了个勉强能用的openapi json

```json
{
    "openapi": "3.1.0",
    "info": {
        "title": "Search Function",
        "description": "Performs a search operation",
        "version": "v1.0.0"
    },
    "servers": [
        {
            "url": "https://google.serper.dev"
        }
    ],
    "paths": {
        "/search": {
            "post": {
                "description": "Execute a search",
                "operationId": "googleSearch",
                "parameters": [],
                "requestBody": {
                    "content": {
                        "application/json": {
                            "schema": {
                                "properties": {
                                    "q": {
                                        "type": "string",
                                        "description": "The search query"
                                    }
                                },
                                "required": [
                                    "q"
                                ]
                            }
                        }
                    },
                    "required": true
                },
                "deprecated": false
            }
        }
    },
    "components": {
        "schemas": {}
    }
}
```

### 搜索结果数据处理

![](assets/1.png)

```python
import json

def main(arg1: str) -> dict:
    try:
        data = json.loads(arg1)
        text_data = json.loads(data['text'])
        organic = text_data.get('organic', [])
        return {
            "result": organic
        }
    except json.JSONDecodeError:
        return {
            "result": []
        }
```