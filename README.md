AI面试官 - 交互式技术演示

一个由我独立开发并部署的AI应用，它能够基于我的简历进行模拟技术面试。

[[Open in Hugging Face Spaces](https://img.shields.io/badge/🤗-Open%20in%20Spaces-blue)](https://huggingface.co/spaces/changqing11/my_ai_chatbot01)
[[Python](https://img.shields.io/badge/Python-3.9+-blue)](https://www.python.org/)

项目亮点

-   多API容灾架构: 集成OpenRouter与DeepSeek双供应商，在一方服务不可用时自动切换，保障应用高可用性。
-   云端部署: 使用Hugging Face Spaces实现一键部署与全球化访问，无需管理服务器。
-   精准提示工程: 通过精心设计的System Prompt，让AI扮演专业的技术面试官，提问紧扣个人技能栈。
-   工程化实践: 采用环境变量管理密钥、依赖管理、异常处理等生产级开发规范。

技术栈

-   后端语言: Python
-   Web框架: Gradio
-   AI服务: OpenRouter API / DeepSeek API
-   部署平台: Hugging Face Spaces
-   版本控制: Git & GitHub

 快速开始

 本地运行

1. 克隆项目并安装依赖：
    ```bash
    git clone [https://github.com/caochangqing11/my-ai-interviewer]
    cd my_ai_chatbot
    pip install -r requirements.txt
    ```

2. 设置环境变量：
    ```bash
    # 复制环境变量示例文件并配置您的API密钥
    cp .env.example .env
    # 在.env文件中填写：OPENROUTER_API_KEY='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'
    ```

3. 启动应用：
    ```bash
    python app.py
    ```

云端部署

1.  Fork本项目到您的GitHub账户
2.  在[Hugging Face Spaces](https://huggingface.co/spaces)创建新Space，连接您的GitHub仓库
3.  在Space的`Settings` -> `Variables`中设置`OPENROUTER_API_KEY`
4.  部署自动完成！🎉

项目架构

```mermaid
graph LR
    A[用户输入] --> B(Gradio UI界面)
    B --> C{Python后端}
    C --> D[OpenRouter API]
    D -- 主线路失败 --> E[DeepSeek API]
    C --> F[异常处理与重试]
    F --> G[返回响应]
    G --> B
 ```   
遇到的问题与解决方案

在开发过程中，我遇到并解决了以下关键问题，这些经历极大地提升了我解决问题和调试的能力：

|            问题              |                                解决方案                                  |
|    Internal Server Error     | 通过分析Hugging Face构建日志，定位到Gradio版本兼容性问题，通过降级至稳定版本（`gradio==3.50.2`）解决。 |
|      API连接超时与故障        | 设计并实现了多API供应商（OpenRouter/DeepSeek）自动切换机制，显著提升了应用的容错能力和鲁棒性。           |
|      环境变量配置错误         | 规范了开发流程，明确了本地开发与云端部署的环境变量配置方法，并在文档中详细说明。                      |
|        中文编码错误           | 在请求中明确指定UTF-8编码（`ensure_ascii=False`），妥善处理了中文字符的传输与 显示。                    |

未来优化方向

-   集成RAG技术：接入个人简历和项目文档库，使AI的提问更具深度和针对性，减少“幻觉”。
-   使用LangChain框架重构：以支持更复杂的AI代理（Agent）流程和多步骤推理。
-   添加对话历史持久化功能：支持面试回放与复盘，帮助用户更好地总结和提高。
-   尝试使用Ollama本地部署：在本地运行量化模型（如Llama 3），以控制成本并减少延迟。

致谢

-   感谢OpenRouter和DeepSeek 提供的优质AI API服务。
-   感谢Hugging Face提供的免费计算资源与便捷的部署平台（Spaces）。
-   感谢所有开源项目的开发者。

---
联系我: [619939394@qq.com]  

简历与更多项目: [https://www.kdocs.cn/l/cpZaaSTt9WTF] [https://huggingface.co/spaces/changqing11/my_ai_chatbot] 一个简易的聊天机器人

