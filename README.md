# 酒别重逢

一个关于自调酒的灵感与知识助手，包含 AI 调酒助手、调研数据可视化和中国自调酒发展历程。

## 技术栈

- **框架**: Next.js 15 (App Router) + TypeScript
- **样式**: Tailwind CSS + shadcn/ui
- **图标**: lucide-react
- **数据可视化**: Apache ECharts (按需加载)
- **AI 服务**: OpenAI API
- **文档渲染**: react-markdown + remark-gfm

## 功能特性

### 1. AI 调酒助手
- 流式对话响应
- 支持模型和温度选择
- Markdown 渲染和代码块复制
- 预置示例问题

### 2. 调研数据可视化
- 口味偏好分布（玫瑰饼图）
- 自调频率 vs 花费散点图
- 工具拥有率雷达图
- 原料 Top10 条形图
- 时间趋势折线图（按月）
- 多维度筛选（年龄段、性别、地区、频率、是否含酒精、味型偏好）

### 3. 发展历程
- 交互式时间线
- Markdown 内容渲染
- 年份节点导航

## 安装与运行

### 1. 安装依赖

```bash
pnpm install
```

### 2. 配置环境变量

复制 `.env.example` 为 `.env.local`：

```bash
cp .env.example .env.local
```

在 `.env.local` 中填入你的 OpenAI API Key：

```
OPENAI_API_KEY=your_openai_api_key_here
```

### 3. 启动开发服务器

```bash
pnpm dev
```

访问 [http://localhost:3000](http://localhost:3000) 查看应用。

### 4. 构建生产版本

```bash
pnpm build
```

### 5. 启动生产服务器

```bash
pnpm start
```

## 项目结构

```
.
├── app/                      # Next.js App Router
│   ├── api/                  # API 路由
│   │   ├── chat/             # AI 聊天 API
│   │   ├── metrics/          # 数据指标 API
│   │   └── history/          # 历史内容 API
│   ├── layout.tsx            # 根布局
│   ├── page.tsx              # 主页面
│   └── globals.css           # 全局样式
├── components/               # React 组件
│   ├── ui/                   # shadcn/ui 基础组件
│   ├── Charts/               # 图表组件
│   ├── ChatPanel.tsx         # 聊天面板
│   ├── Message.tsx           # 消息组件
│   ├── HistoryTimeline.tsx   # 历史时间线
│   └── MDXContent.tsx        # Markdown 内容渲染
├── lib/                      # 工具库
│   ├── openai.ts             # OpenAI 客户端封装
│   ├── echarts.ts            # ECharts 初始化
│   ├── survey.ts             # 调研数据过滤与聚合
│   ├── history.ts            # 历史内容解析
│   ├── rate-limit.ts         # 速率限制
│   └── utils.ts              # 工具函数
└── data/                     # 数据文件
    ├── survey.json           # 调研数据
    └── history.md            # 历史内容
```

## 部署到 Vercel

1. 将代码推送到 GitHub 仓库
2. 在 [Vercel](https://vercel.com) 中导入项目
3. 在项目设置中添加环境变量 `OPENAI_API_KEY`
4. 部署完成

## 开发脚本

- `pnpm dev` - 启动开发服务器
- `pnpm build` - 构建生产版本
- `pnpm start` - 启动生产服务器
- `pnpm lint` - 运行 ESLint
- `pnpm format` - 格式化代码

## 数据模型

### survey.json

每条记录包含以下字段：

- `id`: 唯一标识符
- `ageGroup`: 年龄段 ("18-22" | "23-26" | "27-30")
- `gender`: 性别 ("男" | "女" | "其他/不便透露")
- `region`: 地区（七个地区）
- `frequencyPerWeek`: 每周调酒次数 (0-7)
- `avgCostPerDrink`: 平均每杯花费（人民币）
- `isAlcoholic`: 是否含酒精
- `flavor`: 味型偏好
- `tools`: 工具拥有情况
- `topIngredients`: 常用原料（1-3 个）
- `month`: 调研月份 (YYYY-MM)

### history.md

Markdown 文件，包含 frontmatter 和正文内容：

```markdown
---
items:
  - year: 1920
    title: 标题
    link: https://example.com
---
正文内容...
```

## 性能优化

- 图表组件懒加载
- API 响应缓存
- 图片优化
- 代码分割
- Edge Runtime 优先

## 可访问性

- 所有交互控件具备 label
- 键盘导航支持
- 焦点可见性
- ARIA 标签

## 安全

- API Key 仅在服务端可见
- 基于 IP 的速率限制
- 输入验证（zod）
- CORS 配置

## 许可证

MIT

