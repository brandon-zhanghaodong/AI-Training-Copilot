# AI Training Copilot - 部署指南

## 项目配置完成

本项目已成功从 Google Gemini API 迁移到 DeepSeek API，并配置完成，可以部署到中国国内可访问的环境。

## 主要变更

### 1. API 替换
- ✅ 移除 `@google/genai` 依赖
- ✅ 添加 `openai` SDK（兼容 DeepSeek API）
- ✅ 创建新的 `services/deepseekService.ts` 服务层
- ✅ 更新所有组件引用到新的服务

### 2. 环境配置
- ✅ 创建 `.env.local` 文件配置 API Key
- ✅ 更新 `vite.config.ts` 使用 `DEEPSEEK_API_KEY`
- ✅ 更新 `.gitignore` 保护敏感信息

### 3. 部署配置
- ✅ 创建 `vercel.json` 配置文件
- ✅ 配置构建命令和输出目录
- ✅ 设置环境变量引用

## DeepSeek API 配置

### API Key
```
sk-0c0b90a202cc46fd8932b4f4e451b5c5
```

### API 端点
```
https://api.deepseek.com/v1
```

### 使用的模型
```
deepseek-chat
```

## 部署到 Vercel（推荐）

### 方式一：通过 Vercel Dashboard（最简单）

1. 访问 [Vercel Dashboard](https://vercel.com/dashboard)
2. 点击 "Add New Project"
3. 导入 GitHub 仓库：`brandon-zhanghaodong/AI-Training-Copilot`
4. 配置环境变量：
   - Key: `DEEPSEEK_API_KEY`
   - Value: `sk-0c0b90a202cc46fd8932b4f4e451b5c5`
5. 点击 "Deploy"

### 方式二：通过 Vercel CLI

```bash
# 1. 安装 Vercel CLI（如果未安装）
npm install -g vercel

# 2. 登录 Vercel
vercel login

# 3. 在项目目录下部署
cd /path/to/AI-Training-Copilot
vercel

# 4. 设置环境变量
vercel env add DEEPSEEK_API_KEY

# 5. 部署到生产环境
vercel --prod
```

### 方式三：通过 Git 集成（自动部署）

1. 在 Vercel Dashboard 中连接 GitHub 仓库
2. 启用自动部署
3. 每次推送到 `main` 分支时自动触发部署

## 本地运行

```bash
# 1. 安装依赖
npm install

# 2. 创建 .env.local 文件
echo "DEEPSEEK_API_KEY=sk-0c0b90a202cc46fd8932b4f4e451b5c5" > .env.local

# 3. 启动开发服务器
npm run dev

# 4. 访问 http://localhost:3000
```

## 构建测试

```bash
# 构建生产版本
npm run build

# 预览构建结果
npm run preview
```

## 功能特性

本应用包含以下培训管理功能：

1. **课程生成器（Course Gen）**
   - 根据主题、受众、时长和风格生成课程大纲
   - 支持流式输出
   - Markdown 格式输出

2. **测验生成器（Quiz Gen）**
   - 支持文本和 PDF 文件输入
   - 生成单选题、判断题、多选题
   - 可导出为 CSV 格式

3. **反馈分析（Feedback Insight）**
   - 情感分析（正面/中立/负面）
   - 关键词提取
   - 改进建议生成
   - 可视化图表展示

4. **运营文案助手（Ops Writer）**
   - 生成开课通知邮件
   - 社群预热文案
   - 课程总结与回顾
   - 培训提醒通知

## 中国国内访问

Vercel 在中国国内可以正常访问，部署后的应用可以直接使用，无需额外配置。

### 访问速度优化建议

1. **使用 Vercel 的 Edge Network**
   - Vercel 自动使用全球 CDN
   - 中国用户会被路由到最近的节点

2. **如需更快速度，可考虑：**
   - 使用国内 CDN 服务（如阿里云、腾讯云）
   - 部署到国内云服务商（需要备案）

## 技术栈

- **前端框架**: React 19 + TypeScript
- **构建工具**: Vite 6
- **UI 样式**: TailwindCSS
- **图表库**: Recharts
- **AI API**: DeepSeek (OpenAI 兼容)
- **部署平台**: Vercel

## 注意事项

1. **API Key 安全**
   - 不要将 `.env.local` 提交到 Git
   - 在 Vercel 中使用环境变量管理 API Key
   - 定期更换 API Key

2. **浏览器端 API 调用**
   - 当前配置使用 `dangerouslyAllowBrowser: true`
   - 生产环境建议添加后端代理保护 API Key

3. **API 限制**
   - 注意 DeepSeek API 的调用频率限制
   - 监控 API 使用量和成本

## 下一步优化建议

1. **添加后端 API 层**
   - 使用 Vercel Serverless Functions
   - 保护 API Key 不暴露在前端

2. **添加用户认证**
   - 限制应用访问权限
   - 记录用户使用情况

3. **添加缓存机制**
   - 减少 API 调用次数
   - 提升响应速度

4. **添加错误处理和日志**
   - 更好的错误提示
   - 监控应用健康状态

## 支持

如有问题，请联系项目维护者或提交 GitHub Issue。

---

**部署时间**: 2026-02-02  
**配置人**: Manus AI  
**项目仓库**: https://github.com/brandon-zhanghaodong/AI-Training-Copilot
