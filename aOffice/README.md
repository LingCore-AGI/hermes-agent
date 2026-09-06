<p align="center">
  <img src="aOffice/assets/demo/logo.png" alt="Hermes Agent" width="100%">
</p>

# Hermes Agent 中文灵核桌面端
<p align="center">
  <a href="https://hermes-agent.nousresearch.com/">Hermes官网</a> | <a href="/">Hermes桌面版</a>
</p>
<p align="center">
  <a href="/docs/">
  <img src="https://img.shields.io/badge/weixin-bitcreate-FFD700?style=for-the-badge" alt="Documentation">
  </a>
  <a href="/">
  <img src="https://img.shields.io/badge/build-passing-brightgreen?style=for-the-badge" alt="vx">
  </a>
  <a href="https://github.com/NousResearch/hermes-agent/blob/main/LICENSE">
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License: MIT">
  </a>
  <a href="https://nousresearch.com">
  <img src="https://img.shields.io/badge/Built%20by-Nous%20Research-blueviolet?style=for-the-badge" alt="Built by Nous Research">
  </a>
  <a href="README.zh-CN.md">
  <img src="https://img.shields.io/badge/Lang-中文-red?style=for-the-badge" alt="中文"></a>

</p>

##  ❤️前言

依稀记得2022年11月底，**ChatGPT：引爆大众市场的“第一枪”** 
一晃几年过去了，大模型层出不穷，百家争艳！ai agent应运而生，作为早期使用大模型的用户，选择一款适用、实用的agent尤为重要，尝试了使用各种ai agent后，最终我选择了Hermes，在深度使用hermes的过程中，发现了诸多问题，虽然已经算是很好了，但是还不够好！
于是走向了hermes二次开发之路……
**用牛马去指挥牛马** ----方法可行，但是实操缺难度极大！
也许很多人会先思考，用codex或者是openclaw/workbuddy 去开发hermes岂不是更好，其实不然！真正的到了生产开发环境中，才会知道，大量的token消耗以及需要让大模型去理解整个hermes系统是多么的困难！对于hermes系统进行二次开发，还不如直接让大模型自己写程序呢，但是自己写程序又不会有系统级架构，那么，能站在巨人的肩膀上，又何必下来呢！

## 一、Hermes灵核桌面端

起初是没有那个精力去开发hermes的，只不过用的多了，发现的问题比较多，例如：
1、hermes agent真的能给电脑普通小白用户使用吗？
	回答：至今为止，hermes agent面向普通用户的距离还是很远的，为什么？因为hermes是很多程序员做出来的系统，程序员的认知里会固化一些概念和思维逻辑，他们会认为用户已经知道了这个逻辑，基于这个逻辑，在系统里添砖加瓦！但是普通用户对于这个系统是陌生的，是不知道如何下手让hermes系统为自己工作的！

2、hermes记忆系统到底是什么？为什么我的hermes记忆系统如此混乱？
	回答：我认为hermes的记忆系统是一个半成品，在使用hermes做了很多工作之后，我发现记忆系统记忆非常混乱，而这种混乱非用户自身主动改变的，而是记忆系统自身被动触发的，如果不是在使用的过程中，发现越来越偏离方向，我也不会去扒拉hermes系统记忆模块的实现原理，通过把记忆的代码都通读了一遍，给我的感觉就是：这是一个半成品！即：是为了给大模型带 **“紧箍咒”** 从而为用户更好的工作而设计的一个模块，但是这个模块的设计逻辑，设计过度了，则大量消耗token，浪费很多钱，设计委婉了，节省token了，又会让大模型不会按照用户的意愿来执行工作。当然，如果用户使用过workbuddy或者是其他的ai agent感受会非常明显，不停的在后台自动记录笔记，收集信息！的确让人很不舒服！这些信息本身就是用户的隐私！
3、hermes agent系统安装、更新如此繁琐，对中文又不是很友好，是否可以改善？
	回答：hermes系统的更新迭代速度是非常快的， 这有利有弊，利的方面体现在，有很多人为了这个系统而努力，修改和完善功能！弊端在于，频繁的更新会让整个软件变得非常不稳定，已经安装好hermes的普通用户很可能会因为一次又一次的更新导致软件无法使用！同时，hermes系统对于中文用户并不友好，特别需要中文用户懂一些程序设计的逻辑！
4、hermes agent系统的用户体验怎么样？
	回答：功能完备性是完全没有问题的，但是用户体验上却差了很多，多家ai agent系统在电脑里安装好后，一对比，答案是显而易见的！我个人认为，这主要取决于hermes agent的模版系统特别单一粗糙导致的问题。

 基于以上四个问题，如果单纯的设计一款独立的客户端而偏离hermes内核，这是不可取的！虽然github上已经有人在这样子做了！hermes桌面客户端既要有原生的核心功能更新又要有更好的用户体验，这非常困难，根因是hermes系统设计的架构逻辑，即数据层和模版层是耦合在一起的！
 
    为了解决上面的问题，既要还要又要！hermes灵核桌面端应运而生------采用对于hermes agent系统进行修改一个文件，实现最小的侵入点，，从而达到更好的用户体验以及不破坏原生的任何功能。

### 二、桌面端演示

[<img src="./aOffice/assets/demo/desktop01.png" alt="Hermes Agent 灵核桌面版工作台" width="100%">](./aOffice/assets/demo/desktop01.png)


## 1.Hermes模板截图

hermes灵核桌面端工作台采用分步式设计，对整个hermes原生模版进行了重塑，会话和项目进行了单独隔离，会话条理清晰，项目会话显而易见。

|                                                              桌面端首页（亮色）                                                              |                                                             桌面端首页（暗色）                                                             |
| :---------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------: |
| [<img src="./aOffice/assets/demo/desktop-light.png" alt="Hermes Agent 亮色模板" width="100%">](./aOffice/assets/demo/desktop-light.png) | [<img src="./aOffice/assets/demo/desktop-dark.png" alt="Hermes Agent 暗色模板" width="100%">](./aOffice/assets/demo/desktop-dark.png) |

## 2.记忆管理模块

Hermes 桌面版的"记忆"和"学习经验"，都储存在你电脑上的一个本地文件夹里。这个文件夹的位置取决于你的操作系统：

- **Windows 系统**：`%LOCALAPPDATA%\hermes`（即 `C:\Users\<用户名>\AppData\Local\hermes\`）
- **macOS / Linux 系统**：`~/.hermes`

提示这是一个隐藏文件夹，你可以在文件管理器的地址栏直接输入路径访问。记忆和学习经验相关的核心文件，都存放在这个主目录下的 `memories` 文件夹中。

###### 2.1 MEMORY.md — 工作笔记本

Hermes 的长期记忆和学习经验，主要就体现在 `~/.hermes/memories/` 文件夹下的两个 Markdown 文件里。它们共同构成了一个"会思考、会总结"的记忆系统。

| 属性        | 说明                                                        |
| --------- | --------------------------------------------------------- |
| **文件位置**  | `~/.hermes/memories/MEMORY.md`                            |
| **作用**    | 记录**环境事实、项目经验和工作约定**。比如你项目的技术栈、常用的开发工具、以及解决过的具体问题         |
| **类比**    | "工作笔记本"                                                   |
| **字符上限**  | **2,200 字符**（约 800 tokens）                                |
| **典型条目数** | 8-15 条                                                    |
| **管理方式**  | 由 Agent 通过 `memory` 工具自动管理（add / replace / remove），也可手动干预 |

###### 2.2 USER.md — 用户档案

| 属性        | 说明                                      |
| --------- | --------------------------------------- |
| **文件位置**  | `~/.hermes/memories/USER.md`            |
| **作用**    | 记录**你的个人偏好、沟通风格和习惯**。比如你喜欢的回答风格、你的技术背景等 |
| **类比**    | "用户档案"                                  |
| **字符上限**  | **1,375 字符**（约 500 tokens）              |
| **典型条目数** | 5-10 条                                  |
| **管理方式**  | 由 Agent 通过 `memory` 工具自动管理，也可手动干预       |

重要这两个文件有**严格的字符上限**，这是刻意为之，目的是强制 AI 进行"信息筛选与压缩"，只保留最重要的知识，避免记忆变得臃肿无效。

|                                                            Memory.md记忆管理                                                             |                                                          USER.md记忆管理                                                           |
| :----------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------: |
| [<img src="./aOffice/assets/demo/memory_md.png" alt="Hermes Agent上下文记忆memeory文件" width="100%">](./aOffice/assets/demo/memory_md.png) | [<img src="./aOffice/assets/demo/memory_user.png" alt="Hermes Agent用户画像" width="100%">](./aOffice/assets/demo/memory_user.png) |


#### 3.项目模块

原生的hermes会话和项目是耦合在一起的，没有做单独分离，灵核桌面端直接把项目独立化，后续会持续更新一些成品的项目给用户使用。

|                                                           项目管理界面                                                            |                                                              新建项目页面                                                               |
| :-------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------: |
| [<img src="./aOffice/assets/demo/projects.png" alt="Hermes Agent 项目管理模板" width="100%">](./aOffice/assets/demo/projects.png) | [<img src="./aOffice/assets/demo/project_add.png" alt="Hermes Agent 增加项目模板" width="100%">](./aOffice/assets/demo/project_add.png) |

#### 4.会话模块

|                                                                独立对话框                                                                |                                                              会话内容页                                                               |
| :---------------------------------------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------: |
| [<img src="./aOffice/assets/demo/desktop-light.png" alt="Hermes Agent 亮色模板" width="100%">](./aOffice/assets/demo/desktop-light.png) | [<img src="./aOffice/assets/demo/messages_ss.png" alt="Hermes Agent 会话详情页" width="100%">](./aOffice/assets/demo/messages_ss.png) |


#### 5.记忆时间轴模块

|                                                                 保存会话                                                                 |                                                                    会话保存成功                                                                    |
| :----------------------------------------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------: |
| [<img src="./aOffice/assets/demo/saveMeasage.png" alt="Hermes Agent 时间记忆轴保存会话" width="100%">](./aOffice/assets/demo/saveMeasage.png) | [<img src="./aOffice/assets/demo/insertMeassage.png" alt="Hermes Agent 时间记忆轴插入会话内容" width="100%">](./aOffice/assets/demo/insertMeassage.png) |
|                                                             **注入会话无感知**                                                              |                                                                  **注入会话成功**                                                                  |
|  [<img src="./aOffice/assets/demo/zhuru_meass.png" alt="Hermes Agent 无感知注入会话" width="100%">](./aOffice/assets/demo/zhuru_meass.png)  |   [<img src="./aOffice/assets/demo/ok_zhuru_mess.png" alt="Hermes Agent 会话内容注入成功" width="100%">](./aOffice/assets/demo/ok_zhuru_mess.png)    |

#### 6.快捷工具管理模块

|                                                            快捷工具                                                             |                                                               快捷工具设置                                                                |
| :-------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------: |
| [<img src="./aOffice/assets/demo/qk_tools.png" alt="Hermes Agent 快捷工具区域" width="100%">](./aOffice/assets/demo/qk_tools.png) | [<img src="./aOffice/assets/demo/qk_tools_set.png" alt="Hermes Agent快捷工具设置页" width="100%">](./aOffice/assets/demo/qk_tools_set.png) |
|                                                                                                                             |                                                                                                                                     |

#### 7.机器人聊天群模块

|                                                            点击进入机器人聊天群                                                            |                                                             机器人聊天页面                                                              |
| :------------------------------------------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------: |
| [<img src="./aOffice/assets/demo/bots_index.png" alt="Hermes Agent 机器人聊天入口" width="100%">](./aOffice/assets/demo/bots_index.png) | [<img src="./aOffice/assets/demo/bots_indexs.png" alt="Hermes Agent 机器人页面" width="100%">](./aOffice/assets/demo/bots_indexs.png) |

#### 8.设置管理页面

| ![[Pasted image 20260906222233.png]] |
| ------------------------------------ |

### 三、灵核桌面端亮点

1、采用单点侵入的方式挂载整个模板功能模块，真正实现数据层和模版层分离，后续hermes官方或许会更新到灵核桌面的架构形态。
2、优秀可操作、可查看修改的记忆系统以及模板开发的记忆时间轴模块，节省大量的token消耗，约为原生hermes四分之一，即：节省四分之三的token消耗。
3、良好的用户使用体验，主要体现在：独立会话模块，项目物理隔离模块，随性会话和项目中的会话完全区分开。其次是，实时关注订阅的大模型额度数据，以及快捷工具的使用，快捷工具从根本上已经完美的替代了电脑系统，安装的任何软件，手动设置一下，就可以纳入灵核桌面端，即：一键启动。快捷工具固定了日记本，对于灵核桌面端的使用，可以进行“随手记”功能。
4、原生hermes用户数据和hermes agent源代码耦合在一起，灵核桌面端单独存储用户的数据，永不丢失，重新安装hermes客户端，旧数据可以无缝接入，多次更新失败以及删除源代码重新安装，都不会损失任何用户数据。
5、灵核桌面端高度适配Windows系统，macOS 用户可使用免费AI，对桌面端文件做微小改动即可适配，**一键安装，使用门槛极低** 下载安装后配置 API Key 或本地模型端点即可使用

### 四、下载桌面客户端

Hermes 灵核桌面客户端将会进行持续更新、维护。你可以访问添加下面的微信群了解整个项目的动态，获取使用体验视频进行浏览观看。

扫码加入 Hermes Agent 中文社区微信群； 

[<img src="./aOffice/assets/demo/weixin.png" alt="Hermes Agent 中文社区微信群二维码" width="260">](https://github.com/LingCore-AGI/hermes-agent/tree/main)

## 五、开发环境要求


- [Git](https://git-scm.com/install/windows) - 安装 Git
- [Node.js](https://nodejs.org/) 22+
- [Python](https://python.org)  3.11~3.13
- [llama_cpp](https://github.com/ggml-org/llama.cpp/releases) Windows x64 (CUDA 12) 
- [nomic-embed-text-v1.5-q4_k_m.gguf](https://huggingface.co/RinaChen/nomic-embed-text-v1.5-Q4_K_M-GGUF/tree/main?show_file_info=nomic-embed-text-v1.5-q4_k_m.gguf)  nomic-embed-text-v1.5-q4_k_m.gguf
- [qwen2.5-7b-instruct-q4_k_m.gguf](https://huggingface.co/paultimothymooney/Qwen2.5-7B-Instruct-Q4_K_M-GGUF/tree/main?show_file_info=qwen2.5-7b-instruct-q4_k_m.gguf)  qwen2.5-7b-instruct-q4_k_m.gguf
- [Microsoft C++ Build Tools Visual Studio](https://visualstudio.microsoft.com/zh-hant/visual-cpp-build-tools/) 

## 发布流程

版本使用 SemVer tag：

```text
v0.1.0-alpha.1
v0.1.0-beta.1
v0.1.0
v0.1.1
```
 

## 未来开发方向

- 加强用户体验
- 重构hermes记忆管理系统模块，让记忆真正的具有灵性，可智能管理本地记忆系统。
- 完美适配macOS 与 Windows 的打包和安装行为；
 
---
