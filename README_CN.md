# AI Crypto 对冲基金

这是一个由AI驱动的加密货币版对冲基金的概念验证项目。该项目的目标是探索使用AI Agent进行交易决策的可能性。本项目仅用于**教育和研究**目的，不适用于真实交易或投资。

特别声明：
**本项目不会为任何加密货币（比如 AI Agent Meme）提供背书，也不会作为基础项目发行任何加密货币。**

该系统由多个AI Agent协同工作：

1. 估值代理 - 计算加密货币的内在价值并生成交易信号
2. 情绪代理 - 分析市场情绪并生成交易信号
3. 基本面代理 - 分析基本面数据并生成交易信号
4. 技术分析师 - 分析技术指标并生成交易信号
5. 风险管理者 - 计算风险指标并设定头寸限制
6. 投资组合经理 - 做出最终交易决策并生成订单

<img width="1060" alt="Screenshot 2025-01-03 at 5 39 25 PM" src="https://github.com/user-attachments/assets/4611aace-27d0-43b2-9a70-385b40336e3f" />

注意：该系统模拟交易决策，并不进行实际交易。

## 免责声明

此项目仅用于**教育和研究目的**。

- 不适用于真实交易或投资
- 不提供任何担保或保证
- 过去的表现不代表未来的结果
- 创作者不对任何财务损失承担责任
- 投资决策请咨询财务顾问

使用此软件即表示您同意仅将其用于学习和研究目的。

## 目录
- [设置](#setup)
- [使用](#usage)
  - [运行对冲基金](#running-the-hedge-fund)
  - [运行回测](#running-the-backtester)
- [项目结构](#project-structure)
- [贡献](#contributing)
- [功能请求](#feature-requests)
- [许可证](#license)

## 设置

克隆仓库：
```bash
git clone https://github.com/whitelistlab/ai-crypto-hedge-fund.git
cd ai-crypto-hedge-fund
```

1. 安装Poetry（如果尚未安装）：
```bash
curl -sSL https://install.python-poetry.org | python3 -
```

2. 安装依赖：
```bash
poetry install
```

3. 设置环境变量：
```bash
# 为您的API密钥创建.env文件
cp .env.example .env
```

在.env文件中设置API密钥：
```
# 从https://platform.openai.com/获取您的OpenAI API密钥
OPENAI_API_KEY=your-openai-api-key

# 从https://financialdatasets.ai/获取您的金融数据集API密钥
FINANCIAL_DATASETS_API_KEY=your-financial-datasets-api-key
```

**重要**：您必须设置OpenAI API密钥才能使对冲基金正常工作。

AAPL、GOOGL、MSFT、NVDA和TSLA的金融数据是免费的，不需要API密钥。

对于其他任何股票代码，您需要在.env文件中设置`FINANCIAL_DATASETS_API_KEY`。

## 使用

### 运行对冲基金
```bash
poetry run python src/main.py --ticker AAPL,MSFT,NVDA
```

**示例输出：**
<img width="992" alt="Screenshot 2025-01-06 at 5 50 17 PM" src="https://github.com/user-attachments/assets/e8ca04bf-9989-4a7d-a8b4-34e04666663b" />

您还可以指定`--show-reasoning`标志以将每个代理的推理打印到控制台。

```bash
poetry run python src/main.py --ticker AAPL --show-reasoning
```
您可以选择指定开始和结束日期，以便在特定时间段内做出决策。

```bash
poetry run python src/main.py --ticker AAPL,MSFT,NVDA --start-date 2024-01-01 --end-date 2024-03-01 
```

### 运行回测器

```bash
poetry run python src/backtester.py --ticker AAPL,MSFT,NVDA
```

**示例输出：**
<img width="941" alt="Screenshot 2025-01-06 at 5 47 52 PM" src="https://github.com/user-attachments/assets/00e794ea-8628-44e6-9a84-8f8a31ad3b47" />

您可以选择指定开始和结束日期，以便在特定时间段内进行回测。

```bash
poetry run python src/backtester.py --ticker AAPL,MSFT,NVDA --start-date 2024-01-01 --end-date 2024-03-01
```

## 项目结构 
```
ai-hedge-fund/
├── src/
│   ├── agents/                   # 代理定义和工作流
│   │   ├── fundamentals.py       # 基本面分析代理
│   │   ├── portfolio_manager.py  # 投资组合管理代理
│   │   ├── risk_manager.py       # 风险管理代理
│   │   ├── sentiment.py          # 情绪分析代理
│   │   ├── technicals.py         # 技术分析代理
│   │   ├── valuation.py          # 估值分析代理
│   ├── tools/                    # 代理工具
│   │   ├── api.py                # API工具
│   ├── backtester.py             # 回测工具
│   ├── main.py                   # 主入口
├── pyproject.toml
├── ...
```

## 贡献

1. Fork仓库
2. 创建功能分支
3. 提交您的更改
4. 推送到分支
5. 创建一个Pull Request

**重要**：请保持您的Pull Request小而集中。这将使审查和合并更容易。

## 功能请求

如果您有功能请求，请打开一个[issue](https://github.com/virattt/ai-hedge-fund/issues)并确保其标记为`enhancement`。

## 许可证

此项目根据MIT许可证授权 - 详情请参阅LICENSE文件。
