# 酒别重逢 - 自调酒知识助手网站

一个基于 Next.js 15 的现代化自调酒知识平台，包含 AI 调酒助手、数据可视化和历史发展历程。

## 技术栈

- **框架**: Next.js 15 (App Router)
- **语言**: TypeScript
- **样式**: Tailwind CSS
- **UI 组件**: shadcn/ui, Radix UI
- **图标**: lucide-react
- **图表**: Apache ECharts (按需加载)
- **Markdown 渲染**: react-markdown
- **API 调用**: DeepSeek API

## 本地开发

### 环境要求

- Node.js 18+ 
- npm 或 pnpm

### 安装步骤

1. 克隆仓库并安装依赖：

```bash
npm install
# 或
pnpm install
```

2. 创建环境变量文件 `.env.local`：

```bash
OPENAI_API_KEY=your_deepseek_api_key_here
```

3. 启动开发服务器：

```bash
npm run dev
# 或
pnpm dev
```

4. 访问 [http://localhost:3000](http://localhost:3000)

## Vercel 部署

### 部署步骤

1. 将代码推送到 GitHub/GitLab/Bitbucket

2. 在 [Vercel](https://vercel.com) 导入项目

3. **重要**: 在 Vercel 项目设置中添加环境变量：
   - `OPENAI_API_KEY`: 你的 DeepSeek API 密钥

4. 部署配置会自动检测 Next.js 框架

### 环境变量配置

在 Vercel 项目设置 > Environment Variables 中添加：

```
OPENAI_API_KEY=sk-your-deepseek-api-key
```

### 常见部署问题

1. **构建失败**: 
   - 检查 Node.js 版本（推荐 18+）
   - 确保所有依赖都正确安装
   - 查看 Vercel 构建日志中的具体错误

2. **API 路由错误**:
   - 确保环境变量 `OPENAI_API_KEY` 已正确配置
   - 检查 API 路由的 runtime 设置（Node.js）

3. **文件读取错误**:
   - 确保 `data/` 目录中的文件已提交到 Git
   - 检查文件路径是否正确

## 项目结构

```
├── app/                    # Next.js App Router 页面
│   ├── api/                # API 路由
│   │   ├── chat/          # AI 聊天 API
│   │   ├── metrics/       # 数据统计 API
│   │   └── history/       # 历史数据 API
│   ├── layout.tsx         # 根布局
│   └── page.tsx           # 首页
├── components/            # React 组件
│   ├── ui/               # UI 基础组件
│   ├── Charts/           # 图表组件
│   ├── ChatPanel.tsx     # AI 聊天面板
│   └── HistoryTimeline.tsx # 历史时间线
├── data/                 # 数据文件
│   ├── survey.json      # 调研数据
│   └── history.md       # 历史记录
├── lib/                 # 工具函数
│   ├── openai.ts        # DeepSeek API 封装
│   ├── survey.ts        # 数据过滤和聚合
│   └── history.ts       # 历史数据解析
└── public/              # 静态资源
```

## 功能特性

- ✅ AI 调酒助手（流式对话）
- ✅ 数据可视化（5 种图表）
- ✅ 历史发展历程（时间线展示）
- ✅ 响应式设计（移动端适配）
- ✅ 按需加载（性能优化）

## 开发命令

```bash
npm run dev      # 启动开发服务器
npm run build    # 构建生产版本
npm run start    # 启动生产服务器
npm run lint     # 代码检查
npm run format   # 代码格式化
```

## License

MIT
