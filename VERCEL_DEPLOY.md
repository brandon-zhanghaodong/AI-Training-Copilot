# 🚀 一键部署到 Vercel

## 方法一：点击按钮部署（最快）

点击下面的按钮，一键部署到 Vercel：

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fbrandon-zhanghaodong%2FAI-Training-Copilot&env=DEEPSEEK_API_KEY&envDescription=DeepSeek%20API%20Key%20for%20AI%20model%20access&envLink=https%3A%2F%2Fplatform.deepseek.com&project-name=ai-training-copilot&repository-name=ai-training-copilot)

### 部署步骤：

1. **点击上面的按钮**
   - 会跳转到 Vercel 部署页面
   - 如果未登录，需要先登录 Vercel

2. **配置仓库**
   - 选择 Git 提供商（GitHub）
   - 授权 Vercel 访问你的 GitHub

3. **配置环境变量**
   - 在弹出的表单中填写：
     ```
     DEEPSEEK_API_KEY = sk-0c0b90a202cc46fd8932b4f4e451b5c5
     ```

4. **点击 Deploy**
   - 等待 2-3 分钟
   - 部署完成后会显示访问链接

5. **访问应用**
   - 点击 "Visit" 按钮
   - 开始使用 AI Training Copilot

---

## 方法二：从 Vercel Dashboard 导入

### 步骤 1：访问 Vercel Dashboard

打开浏览器，访问：https://vercel.com/new

### 步骤 2：导入 Git 仓库

1. 在 "Import Git Repository" 部分
2. 输入仓库 URL：
   ```
   https://github.com/brandon-zhanghaodong/AI-Training-Copilot
   ```
3. 点击 "Import"

### 步骤 3：配置项目

| 配置项 | 值 |
|--------|-----|
| Project Name | `ai-training-copilot` |
| Framework Preset | Vite |
| Root Directory | `./` |
| Build Command | `npm run build` |
| Output Directory | `dist` |

### 步骤 4：添加环境变量

点击 "Environment Variables" 展开，添加：

```
Name: DEEPSEEK_API_KEY
Value: sk-0c0b90a202cc46fd8932b4f4e451b5c5
```

选择所有环境：
- ✅ Production
- ✅ Preview
- ✅ Development

### 步骤 5：部署

1. 点击 "Deploy" 按钮
2. 等待构建完成（约 2-3 分钟）
3. 部署成功后，会显示：
   - ✅ 部署 URL（如：`https://ai-training-copilot.vercel.app`）
   - 📊 部署详情和日志

### 步骤 6：访问应用

点击部署 URL，开始使用！

---

## 方法三：使用 Vercel CLI

### 前置要求
- 已安装 Node.js 16+
- 已安装 Git

### 步骤 1：安装 Vercel CLI

```bash
npm install -g vercel
```

### 步骤 2：克隆仓库

```bash
git clone https://github.com/brandon-zhanghaodong/AI-Training-Copilot.git
cd AI-Training-Copilot
```

### 步骤 3：登录 Vercel

```bash
vercel login
```

会打开浏览器进行授权，按照提示完成登录。

### 步骤 4：首次部署

```bash
vercel
```

按照提示操作：

```
? Set up and deploy "~/AI-Training-Copilot"? [Y/n] Y
? Which scope do you want to deploy to? <选择你的账号>
? Link to existing project? [y/N] N
? What's your project's name? ai-training-copilot
? In which directory is your code located? ./
? Want to override the settings? [y/N] N
```

### 步骤 5：添加环境变量

```bash
vercel env add DEEPSEEK_API_KEY
```

按照提示：
1. 输入值：`sk-0c0b90a202cc46fd8932b4f4e451b5c5`
2. 选择环境：
   - ✅ Production
   - ✅ Preview  
   - ✅ Development

### 步骤 6：部署到生产环境

```bash
vercel --prod
```

等待部署完成，会显示生产环境 URL。

---

## 部署后验证

### 1. 检查部署状态

访问 Vercel Dashboard：
- https://vercel.com/dashboard

查看项目部署状态：
- ✅ 部署成功
- 📊 查看构建日志
- 🌐 获取部署 URL

### 2. 测试功能

访问部署的应用，测试各个功能：

#### 测试课程生成器
1. 点击 "课程生成" 标签
2. 输入培训主题：`销售谈判技巧`
3. 点击 "生成课程大纲"
4. 查看是否正常生成内容

#### 测试测验生成器
1. 点击 "试题生成" 标签
2. 输入一段文本或上传 PDF
3. 点击 "生成试题"
4. 查看是否正常生成题目

#### 测试反馈分析
1. 点击 "反馈洞察" 标签
2. 输入一些反馈文本
3. 点击 "智能分析洞察"
4. 查看情感分析和关键词

#### 测试运营文案
1. 点击 "运营文案" 标签
2. 输入培训信息
3. 点击 "一键生成文案"
4. 查看生成的文案

### 3. 检查 API 调用

打开浏览器开发者工具（F12）：
- 查看 Network 标签
- 确认 API 请求正常
- 检查是否有错误

---

## 常见问题

### Q1: 部署失败怎么办？

**A:** 检查以下几点：
1. 环境变量是否正确配置
2. 查看构建日志中的错误信息
3. 确认 DeepSeek API Key 是否有效
4. 检查 GitHub 仓库是否可访问

### Q2: 部署成功但无法访问？

**A:** 可能原因：
1. 等待几分钟，DNS 传播需要时间
2. 清除浏览器缓存
3. 尝试使用无痕模式访问
4. 检查 Vercel 部署状态

### Q3: API 调用失败？

**A:** 检查：
1. DeepSeek API Key 是否正确
2. API Key 是否有足够的额度
3. 网络连接是否正常
4. 查看浏览器控制台错误信息

### Q4: 如何更新部署？

**A:** 有两种方式：

**方式 1：自动部署（推荐）**
- Vercel 会自动监听 GitHub 仓库
- 推送代码到 `main` 分支会自动触发部署

**方式 2：手动部署**
```bash
cd AI-Training-Copilot
git pull origin main
vercel --prod
```

### Q5: 如何查看日志？

**A:** 三种方式：

1. **Vercel Dashboard**
   - 访问 https://vercel.com/dashboard
   - 选择项目 → Deployments
   - 点击具体部署查看日志

2. **Vercel CLI**
   ```bash
   vercel logs <deployment-url>
   ```

3. **实时日志**
   ```bash
   vercel logs --follow
   ```

### Q6: 如何自定义域名？

**A:** 在 Vercel Dashboard：
1. 选择项目
2. 进入 "Settings" → "Domains"
3. 添加自定义域名
4. 按照提示配置 DNS

### Q7: 如何回滚到之前的版本？

**A:** 在 Vercel Dashboard：
1. 选择项目 → Deployments
2. 找到要回滚的版本
3. 点击 "..." → "Promote to Production"

---

## 部署成功后的下一步

### 1. 配置自定义域名（可选）
- 在 Vercel 中添加自定义域名
- 配置 DNS 记录
- 启用 HTTPS（自动）

### 2. 设置团队协作（可选）
- 邀请团队成员
- 配置访问权限
- 设置部署通知

### 3. 监控和分析
- 查看访问统计
- 监控 API 使用量
- 设置告警通知

### 4. 优化性能
- 启用 Edge Functions
- 配置缓存策略
- 优化图片和资源

---

## 技术支持

如遇到问题，可以：
1. 查看 [完整部署指南](./DEPLOYMENT_GUIDE.md)
2. 提交 [GitHub Issue](https://github.com/brandon-zhanghaodong/AI-Training-Copilot/issues)
3. 查看 [Vercel 文档](https://vercel.com/docs)

---

**祝部署顺利！** 🎉

如果部署成功，别忘了：
- ⭐ Star 本项目
- 🔗 分享给需要的同事
- 💬 提供反馈和建议
