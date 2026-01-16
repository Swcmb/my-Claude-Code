# my-AI-Agent

一个用约200行代码实现的轻量级AI编程助手，灵感来源于对现有AI编程工具核心原理的研究。

## 简介

my-AI-Agent 是一个简单的编程代理实现，展示了AI编程助手背后的基本原理。该项目证明了看似复杂的AI编程助手实际上可以通过简单的工具和循环逻辑实现。

核心思想是：AI模型不直接访问文件系统，而是请求操作，由本地代码执行这些操作，结果再返回给AI模型进行下一步决策。

## 功能特性

- **读取文件**: 让AI能够查看项目中的文件内容
- **列出文件**: 使AI能够在项目目录间导航
- **编辑文件**: 允许AI创建和修改文件内容
- **工具化交互**: 通过结构化工具调用来执行任务

## 架构设计

系统由以下组件构成：

1. **工具层**: 实现对文件系统的访问（读取、写入、列目录）
2. **工具注册表**: 管理可用工具的中央注册表
3. **系统提示**: 动态生成工具描述并提供给AI模型
4. **工具调用解析器**: 解析AI模型的工具调用请求
5. **代理循环**: 核心交互循环，处理用户输入和AI响应

## 安装与使用

### 环境要求

- Python 3.7+
- Anthropic API客户端或其他LLM提供商
- python-dotenv

### 安装步骤

1. 克隆仓库
2. 安装依赖包
3. 设置环境变量

```
pip install anthropic python-dotenv
```

创建 `.env` 文件并添加API密钥：

```
ANTHROPIC_API_KEY=your_api_key_here
```

### 运行

```
python main.py
```

## 使用示例

启动程序后，您可以与AI助手进行对话：

```
You:> 创建一个hello.py文件，写入Hello World程序
Assistant:> tool: edit_file({"path": "hello.py", "old_str": "", "new_str": "print('Hello World')"})
...
```

多步骤交互示例：
```
You:> 编辑hello.py并添加一个用于乘以两个数字的函数
Assistant:> tool: read_file({"filename": "hello.py"})
Assistant:> tool: edit_file({"path": "hello.py", "old_str": "print('Hello World')", "new_str": "print('Hello World')\n\ndef multiply(a, b):\n    return a * b"})
...
```

## 设计理念

这个项目的目的是展示AI编程助手的核心概念：

- AI模型仅提供指导，实际文件操作由本地代码执行
- 安全的沙盒环境，防止AI直接修改意外文件
- 简洁的架构，易于理解和扩展
- 工具驱动的交互模式

## 扩展建议

有兴趣的开发者可以考虑添加以下功能：

- 更多文件操作工具
- 错误处理和恢复机制
- 上下文感知的文件摘要
- 命令执行工具
- 代码质量检查工具
- 流式响应以获得更好的用户体验

## 贡献

欢迎提交Issue和Pull Request来改进项目。

## 许可证

MIT License

###### ** From https://www.mihaileric.com/The-Emperor-Has-No-Clothes/ **
