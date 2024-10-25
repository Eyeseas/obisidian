---
title: 前端面试anki卡片分享
share: "true"
date: 2024-10-07 22:58
updated: 2024-10-07 22:58
tags:
  - anki
  - AI
  - pupeteer
  - nodejs
categories:
  - tech
  - ai
---
> 卡片数据来源 [前端面试指南-基础篇](https://interview.poetries.top/docs/base.html)


<!-- more -->

## 资源地址

目前是有365张卡片,直链导入
```
https://alist.kong.vision/d/r2/public/anki/fe-base.colpkg
```

## 内容展示
### 桌面端
![image.png](https://alist.kong.vision/d/r2/_imageStore/2024/10/07/20241007225910.png)


### 移动端（ios）
![image.png](https://alist.kong.vision/d/r2/_imageStore/2024/10/07/20241007225957.png)


## 说明

卡片内容比较碎片化，适合利用空闲时间补充一些小的知识点，尽量带上自己的思考去看这些卡片，成体系的学习更重要

## 后记

> 国庆在家闲着，写着玩的玩具代码，之前刷前端面经的时候会用 **anki**卡片记一些知识点，于是有了以下内容:

### 数据源
- https://interview.poetries.top/docs/base.html

### 采集方式
- nodejs + pupeteer + 瞎写的规则  =  一份json数据

采集规则还有很大问题，不能覆盖所有情况，并且如果有些知识点的内容有图片，由于没有做特殊处理，在卡片里面也无法展示，抱歉了哈哈哈

### 制作anki卡片
[ankiConnect插件](https://ankiweb.net/shared/info/2055492159) 提供一系列本地接口管理anki

[details="nodejs创建卡片"]
```javascript
async function createNotes(deckName: string, subSections: NoteOriginal[]): Promise<void> {
    const notes = subSections.map(item => ({
        "deckName": deckName,
        "modelName": "Basic",
        "fields": {
            "Front": item.title,
            "Back": item.content,
        },
        "tags": item.tags,
        "options": {
            "allowDuplicate": false,
            "duplicateScope": "deck",
            "duplicateScopeOptions": {
                "deckName": deckName,
                "checkChildren": false,
                "checkAllModels": false
            }
        }
    }));

    await invoke("addNotes", 6, { notes });
}

export async function createDecks(): Promise<void> {
    for (const item of DeckData) {
        const deck = { deck: item.title };
        await invoke('createDeck', 6, deck);

        if (item.subSections && item.subSections.length > 0) {
            await createNotes(item.title, item.subSections);
        }
    }
}

```
[/details]

### 通过AI给每条数据打标签
> 使用gpt-4o + 简易prompt + nodejs + langChain给每条卡片数据分析总结后都打上了4个tag，缺乏一致性哈哈哈，但是省时省力，正好看了看js/langChain的文档简单的尝试了一下

![image.png](https://alist.kong.vision/d/r2/_imageStore/2024/10/07/20241007230107.png)



[details="langChain代码"]
```js
const model = new ChatOpenAI({
    model: "gpt-4o",
    apiKey: process.env.OPENAI_API_KEY,
    timeout: 10000
}, {
    baseURL: process.env.OPENAI_API_BASE_URL, 
});

const parser = new JsonOutputParser();

const promptTemplate = ChatPromptTemplate.fromMessages([
    ["system", "分析文本内容, 总结出4个合适技术类型的label,使用数组输出,要求尽量短,最好是一个单词,使用英语:"],
    ["user", "{text}"],
]);


const llmChain = promptTemplate.pipe(model).pipe(parser);
```

[/details]


## 完~