# PyClaw Starter

一个 Python 版本的龙虾（PyCrawl）爬虫脚手架项目，基于 LLM 的智能 Web 爬虫框架。

## 核心架构

```
┌─────────────────────────────────────────────────────────────┐
│                      PyClaw 架构                             │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐  │
│  │  记忆管理   │  │  ReAct 引擎  │  │   上下文管理器      │  │
│  │  (Memory)   │  │  (Engine)   │  │    (Context)        │  │
│  └─────────────┘  └─────────────┘  └─────────────────────┘  │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐  │
│  │  页面解析   │  │  任务调度   │  │   配置管理          │  │
│  │  (Parser)   │  │  (Scheduler)│  │    (Config)         │  │
│  └─────────────┘  └─────────────┘  └─────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

## 模块说明

### 🧠 记忆管理 (Memory Manager)
- **短期记忆**：维护当前会话的浏览历史和上下文
- **长期记忆**：持久化存储重要信息和用户偏好
- **向量检索**：基于嵌入的语义搜索和记忆召回

### ⚙️ ReAct 引擎 (ReAct Engine)
- **推理 (Reasoning)**：基于 LLM 的任务分解和决策
- **行动 (Acting)**：执行导航、点击、提取等操作
- **观察 (Observation)**：解析页面内容并更新状态

### 📝 上下文管理 (Context Manager)
- **Token 优化**：智能压缩和上下文窗口管理
- **状态追踪**：维护爬虫执行状态和进度
- **多轮对话**：支持复杂的交互式任务

### 🕷️ 页面解析 (Page Parser)
- **DOM 解析**：提取页面结构和元数据
- **内容清洗**：去除噪声，提取正文
- **链接提取**：智能识别有效链接

### 📅 任务调度 (Task Scheduler)
- **优先级队列**：基于重要性的任务排序
- **并发控制**：可配置的并发限制
- **重试机制**：失败任务的自动重试

### ⚙️ 配置管理 (Config Manager)
- **灵活配置**：YAML/JSON 配置文件支持
- **环境变量**：敏感信息的環境变量管理
- **热重载**：配置变更无需重启

## 快速开始

### 安装

```bash
# 克隆项目
git clone https://github.com/xudongdong/pyclaw-starter.git
cd pyclaw-starter

# 安装依赖
pip install -r requirements.txt
```

### 配置

```bash
# 复制配置模板
cp config.example.yaml config.yaml

# 设置 API Key
export OPENAI_API_KEY="your-api-key"
```

### 运行

```bash
# 启动爬虫
python main.py

# 或使用命令行参数
python main.py --url "https://example.com" --task "提取所有文章标题"
```

## 项目结构

```
pyclaw-starter/
├── config/              # 配置文件
├── src/
│   ├── memory/          # 记忆管理模块
│   ├── engine/          # ReAct 引擎
│   ├── context/         # 上下文管理
│   ├── parser/          # 页面解析
│   └── scheduler/       # 任务调度
├── tests/               # 测试用例
├── examples/            # 示例脚本
└── docs/                # 文档
```

## 示例

```python
from pyclaw import PyCrawl

# 创建爬虫实例
crawler = PyCrawl(
    api_key="your-api-key",
    model="gpt-4",
    max_iterations=10
)

# 执行任务
result = crawler.run(
    url="https://example.com",
    task="查找并总结所有产品信息"
)

print(result.summary)
```

## 许可证

MIT License
