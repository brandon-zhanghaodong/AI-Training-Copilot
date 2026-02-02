# 🚀 AI Training Copilot - 完整部署指南

## ✅ 项目配置完成清单

- [x] API 从 Google Gemini 迁移到 DeepSeek
- [x] 更新所有服务层和组件引用
- [x] 配置环境变量和构建配置
- [x] 创建 Vercel 部署配置
- [x] 添加后端 API 代理保护 API Key
- [x] 推送代码到 GitHub
- [x] 准备部署文档

## 📋 快速部署（推荐方式）

### 方式一：Vercel Dashboard 部署（最简单）

1. **访问 Vercel Dashboard**
   - 打开 https://vercel.com/dashboard
   - 使用 GitHub 账号登录

2. **导入项目**
   - 点击 "Add New Project"
   - 选择 "Import Git Repository"
   - 搜索并选择 `brandon-zhanghaodong/AI-Training-Copilot`

3. **配置项目**
   - **Framework Preset**: Vite
   - **Root Directory**: `./`
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist`

4. **添加环境变量**
   ```
   Key: DEEPSEEK_API_KEY
   Value: sk-0c0b90a202cc46fd8932b4f4e451b5c5
   ```

5. **部署**
   - 点击 "Deploy" 按钮
   - 等待 2-3 分钟完成部署
   - 获得部署 URL（如：`https://ai-training-copilot.vercel.app`）

### 方式二：Vercel CLI 部署

```bash
# 1. 安装 Vercel CLI
npm install -g vercel

# 2. 登录 Vercel（会打开浏览器进行授权）
vercel login

# 3. 进入项目目录
cd AI-Training-Copilot

# 4. 部署到 Vercel（首次部署）
vercel

# 按照提示操作：
# - Set up and deploy? Yes
# - Which scope? 选择你的账号/团队
# - Link to existing project? No
# - What's your project's name? ai-training-copilot
# - In which directory is your code located? ./
# - Want to override the settings? No

# 5. 添加环境变量
vercel env add DEEPSEEK_API_KEY
# 输入值：sk-0c0b90a202cc46fd8932b4f4e451b5c5
# 选择环境：Production, Preview, Development (全选)

# 6. 部署到生产环境
vercel --prod
```

### 方式三：GitHub 自动部署

1. **在 Vercel 中连接 GitHub 仓库**
   - 访问 Vercel Dashboard
   - 导入 `brandon-zhanghaodong/AI-Training-Copilot` 仓库
   - 配置环境变量（同方式一）

2. **启用自动部署**
   - Vercel 会自动监听 `main` 分支
   - 每次推送代码会自动触发部署
   - Pull Request 会创建预览部署

## 🔧 本地开发

### 环境要求
- Node.js 16+ 
- npm 或 pnpm

### 启动步骤

```bash
# 1. 克隆仓库
git clone https://github.com/brandon-zhanghaodong/AI-Training-Copilot.git
cd AI-Training-Copilot

# 2. 安装依赖
npm install

# 3. 创建环境变量文件
cat > .env.local << EOF
DEEPSEEK_API_KEY=sk-0c0b90a202cc46fd8932b4f4e451b5c5
EOF

# 4. 启动开发服务器
npm run dev

# 5. 访问 http://localhost:3000
```

### 构建测试

```bash
# 构建生产版本
npm run build

# 预览构建结果
npm run preview
```

## 🔐 安全性说明

### 当前实现（开发版）
- ✅ 使用客户端直接调用 DeepSeek API
- ⚠️ API Key 暴露在浏览器端（通过环境变量）
- ✅ 适合快速原型和测试

### 生产环境推荐（安全版）
- ✅ 使用后端 API 代理（已创建 `/api/chat.ts`）
- ✅ API Key 保存在服务器端环境变量
- ✅ 前端通过 `/api/chat` 调用，不暴露 API Key

### 切换到安全版本

如需使用安全版本，将所有组件中的服务引用从：
```typescript
import { ... } from '../services/deepseekService';
```

改为：
```typescript
import { ... } from '../services/deepseekService_secure';
```

然后重新部署即可。

## 🌍 中国国内访问

### Vercel 在中国的可用性
- ✅ Vercel 在中国大陆可以访问
- ✅ 使用全球 CDN，自动路由到最近节点
- ✅ 无需额外配置或代理

### 访问速度优化
1. **使用 Vercel Edge Network**（默认启用）
2. **优化静态资源**：图片、字体等
3. **启用 Gzip/Brotli 压缩**（Vercel 自动启用）

### 如需更快速度
- 考虑使用国内 CDN（阿里云、腾讯云）
- 或部署到国内云服务商（需要 ICP 备案）

## 📊 功能模块

### 1. 课程生成器（Course Gen）
- 📝 根据主题、受众、时长、风格生成课程大纲
- 🔄 支持流式输出，实时显示
- 📄 Markdown 格式，易于复制和编辑

### 2. 测验生成器（Quiz Gen）
- 📄 支持文本输入和 PDF 文件上传
- ❓ 生成单选题、判断题、多选题
- 📊 可导出为 CSV 格式，导入题库系统

### 3. 反馈分析（Feedback Insight）
- 📈 情感分析：正面/中立/负面比例
- 🔑 关键词提取：识别高频词汇
- 💡 改进建议：AI 生成可执行建议
- 📊 可视化图表：饼图展示情感分布

### 4. 运营文案助手（Ops Writer）
- 📧 开课通知邮件
- 💬 社群/钉钉预热文案
- 📝 课程总结与回顾
- ⏰ 培训提醒通知

## 🛠 技术栈

| 类别 | 技术 | 版本 |
|------|------|------|
| 前端框架 | React | 19.2.3 |
| 语言 | TypeScript | 5.8.2 |
| 构建工具 | Vite | 6.2.0 |
| UI 库 | TailwindCSS | - |
| 图表 | Recharts | 3.7.0 |
| AI API | DeepSeek | v1 |
| 部署 | Vercel | - |

## 📁 项目结构

```
AI-Training-Copilot/
├── api/                      # Vercel Serverless Functions
│   └── chat.ts              # API 代理端点（保护 API Key）
├── components/              # React 组件
│   ├── CourseGen.tsx       # 课程生成器
│   ├── QuizGen.tsx         # 测验生成器
│   ├── FeedbackInsight.tsx # 反馈分析
│   └── OpsWriter.tsx       # 运营文案助手
├── services/                # 服务层
│   ├── deepseekService.ts  # DeepSeek API 服务（客户端）
│   └── deepseekService_secure.ts # 安全版本（通过后端代理）
├── App.tsx                  # 主应用组件
├── index.tsx               # 应用入口
├── types.ts                # TypeScript 类型定义
├── vite.config.ts          # Vite 配置
├── vercel.json             # Vercel 部署配置
├── package.json            # 项目依赖
├── .env.local              # 本地环境变量（不提交到 Git）
└── .gitignore              # Git 忽略文件
```

## 🔑 环境变量

### 必需变量

| 变量名 | 说明 | 示例值 |
|--------|------|--------|
| `DEEPSEEK_API_KEY` | DeepSeek API 密钥 | `sk-0c0b90a202cc46fd8932b4f4e451b5c5` |

### 配置位置

- **本地开发**: `.env.local` 文件
- **Vercel 部署**: Dashboard → Project Settings → Environment Variables

## 📈 监控和维护

### 查看部署状态
```bash
# 查看最近的部署
vercel ls

# 查看特定部署的日志
vercel logs <deployment-url>
```

### 查看实时日志
1. 访问 Vercel Dashboard
2. 选择项目
3. 进入 "Deployments" 标签
4. 点击具体部署查看日志

### API 使用监控
- 登录 DeepSeek 控制台
- 查看 API 调用量和费用
- 设置使用限额和告警

## ⚠️ 注意事项

### API Key 安全
- ❌ 不要将 `.env.local` 提交到 Git
- ✅ 在 Vercel 中使用环境变量
- ✅ 定期更换 API Key
- ✅ 生产环境使用后端代理

### API 限制
- 注意 DeepSeek API 的调用频率限制
- 监控 API 使用量和成本
- 考虑添加请求缓存机制

### 浏览器兼容性
- 支持现代浏览器（Chrome, Firefox, Safari, Edge）
- 需要支持 ES6+ 和 Fetch API

## 🚀 下一步优化

### 短期优化
- [ ] 添加加载状态和错误提示
- [ ] 添加请求缓存机制
- [ ] 优化移动端响应式布局
- [ ] 添加使用教程和示例

### 中期优化
- [ ] 切换到安全版本（后端 API 代理）
- [ ] 添加用户认证和权限管理
- [ ] 添加使用统计和分析
- [ ] 支持更多文件格式（Word, Excel）

### 长期优化
- [ ] 添加多语言支持
- [ ] 集成更多 AI 模型
- [ ] 添加协作功能
- [ ] 开发移动应用

## 📞 支持和反馈

- **GitHub Issues**: https://github.com/brandon-zhanghaodong/AI-Training-Copilot/issues
- **项目仓库**: https://github.com/brandon-zhanghaodong/AI-Training-Copilot

## 📄 许可证

本项目使用 MIT 许可证。

---

**配置完成时间**: 2026-02-02  
**配置人**: Manus AI  
**DeepSeek API**: https://api.deepseek.com  
**Vercel 平台**: https://vercel.com
