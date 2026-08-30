# LangChain 多功能智能助手

这是一个独立的 Jupyter Notebook 示例，使用 LangChain Agent 将多个 Python 工具组合成一个中文多功能助手。

Notebook：`06-实战：多功能智能助手.ipynb`

## 支持的功能

- 城市天气查询（示例数据）
- 数学表达式计算
- 当前时间、日期和星期查询
- 货币转换（示例汇率）
- 产品与新闻信息搜索（示例数据）

## 安装依赖

```bash
pip install langchain langchain-deepseek python-dotenv rich jupyter
```

## 配置 DeepSeek

在运行 Notebook 前设置环境变量，或在项目目录创建 `.env`：

```env
DEEPSEEK_API_KEY=your_api_key_here
DEEPSEEK_BASE_URL=https://api.deepseek.com
```

不要提交包含真实 API Key 的 `.env` 文件。

## 运行

```bash
jupyter notebook
```

打开 `06-实战：多功能智能助手.ipynb`，按顺序运行各个单元。Notebook 最后会先运行演示问题，然后进入交互模式；输入 `quit` 退出，输入 `reset` 清空对话历史。

## 说明

本示例中的天气、汇率、产品和新闻数据均为代码内置的演示数据，并不代表实时信息。数学工具使用受限的表达式环境，生产环境仍应使用更严格的计算器实现。

## 许可证

[MIT](LICENSE)
