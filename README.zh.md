# LangChain 多功能智能助手

[English](README.md) | 简体中文

使用单个 Jupyter Notebook 演示 LangChain `create_agent` 如何选择 Python 工具并维护对话历史。项目接入 DeepSeek，以中文交互组合天气、数学计算、时间、货币转换和信息查询五类工具。

这是教学示例。天气、汇率、产品和新闻均来自代码内置的示例数据，即使部分工具描述写有“实时”，也不代表接入了实时服务。日期时间工具读取本机时钟。

## 演示内容

- `get_weather`：北京、上海、深圳、成都、杭州、广州的示例天气。
- `calculator`：基本运算及 `sqrt`、`pow`、`abs`、三角函数、对数等部分数学函数。
- `get_time_info`：本地当前时间、今天、明天、昨天和星期。
- `convert_currency`：基于固定汇率字典，在 CNY、USD、EUR、GBP、JPY、HKD 间换算。
- `search_info`：对示例产品和新闻字典做关键词匹配，不执行联网搜索。
- `SmartAssistant`：中文系统提示词、工具注册、Agent 调用、对话历史及重置逻辑。

## 环境与配置

使用兼容所安装 LangChain 和 Jupyter 软件包的 Python 环境。仓库没有固定依赖版本、锁文件或 Python 版本声明，尚未定义可复现的安装环境。

```bash
git clone https://github.com/Daredevil3210/langchain-multifunction-assistant.git
cd langchain-multifunction-assistant
python -m pip install langchain langchain-deepseek python-dotenv rich jupyter
```

启动 Jupyter 前设置环境变量，或在仓库根目录创建本地 `.env`：

```dotenv
DEEPSEEK_API_KEY=replace_with_your_private_key
DEEPSEEK_BASE_URL=https://api.deepseek.com
```

初始化单元目前使用 `deepseek-v4-flash`，并传入 `thinking.type=disabled`。这是 Notebook 中配置的标识，不代表所有账号均可使用。如需更换，应修改该单元并选择支持本项目工具调用及请求参数的模型。`load_dotenv()` 使用默认行为，已有进程环境变量优先于 `.env`。

真实 `.env` 仅保留在本地。模型演示会把提示词和工具结果发送到配置的服务，并可能产生 API 费用。

## 运行

```bash
jupyter notebook
```

打开 [`06-实战：多功能智能助手.ipynb`](06-实战：多功能智能助手.ipynb)，选择安装依赖的内核，按顺序运行各单元。最后一个单元先执行四个演示问题，随后重置对话并进入交互模式。

- 输入 `quit` 退出。
- 输入 `reset` 清空助手消息历史。

示例问题：

```text
北京今天天气怎么样？
帮我算一下 (25 + 17) * 3
现在几点了？
100 美元等于多少人民币？
```

## 仓库结构

- `06-实战：多功能智能助手.ipynb`：模型初始化、工具定义、`SmartAssistant`、演示及交互入口。
- `README.md` / `README.zh.md`：英文与中文说明。
- `LICENSE`：MIT 许可及教程贡献者版权声明。

## 检查方式与限制

演示问题是手工示例，不是自动测试。仓库没有测试运行配置；本次文档更新不宣称已执行 Notebook 或验证 API。

计算器使用关闭内置函数、仅提供部分函数的 Python `eval`。这是教学实现，不是经过加固的表达式解析器，不应接收不可信表达式。对话历史仅保存在 `SmartAssistant` 对象中，没有持久化存储。示例数据可能过时，不能作为实时信息使用。

## 学习背景与许可

Notebook 将自身标为 LangChain 1.2 实战练习。仓库保留 [MIT License](LICENSE) 及 `Copyright (c) 2026 LangChain 1.2 Tutorial contributors` 声明。
