# MindMap AI — 5分钟上线指南

## 文件结构
```
mindmap-deploy/
├── index.html       ← 完整前端（已内嵌所有逻辑）
├── api/
│   └── mindmap.js   ← 后端代理（20行，保护 API Key）
├── vercel.json      ← Vercel 路由配置
└── package.json
```

---

## 部署步骤

### 第一步：拿到 Anthropic API Key
1. 打开 https://console.anthropic.com
2. 注册/登录（可以用 Google）
3. 左侧 → API Keys → Create Key
4. 复制 `sk-ant-api03-xxxxxx` 保存好

### 第二步：上传到 GitHub
1. 打开 https://github.com → New repository
2. 仓库名：`mindmap-ai`，Private（选私有）
3. 上传这4个文件（直接拖进去）

### 第三步：Vercel 一键部署
1. 打开 https://vercel.com → Sign up with GitHub
2. 点 **Add New → Project**
3. 选你的 `mindmap-ai` 仓库 → Import
4. 直接点 **Deploy**（不需要改任何设置）

### 第四步：添加 API Key（关键）
部署完成后：
1. 进入项目 → **Settings → Environment Variables**
2. 点 Add New：
   - Name: `ANTHROPIC_API_KEY`
   - Value: `sk-ant-api03-xxxxxx`（你的key）
   - Environments: 全选 ✓
3. 点 Save

### 第五步：重新部署（让 Key 生效）
1. 进入 **Deployments** 标签
2. 点最新那条右边的 `···` → **Redeploy**

### 完成！
你的网址：`https://mindmap-ai-xxx.vercel.app`

---

## 验证是否成功
打开网站 → 粘贴任意文字 → 点 Generate Mind Map
- ✅ 成功：右边出现思维导图
- ❌ 失败：底部状态栏显示错误信息

常见问题：
- `HTTP 401` → API Key 填错了
- `HTTP 429` → API 额度用完（去 console 充值）
- 没反应 → 检查 Redeploy 是否做了

---

## 费用
| 项目 | 费用 |
|------|------|
| Vercel 托管 | 免费（个人够用） |
| 每次生成导图 | ~$0.001 |
| 每月1000次 | ~$1 |

---

## 如果想要自定义域名
1. 在 Vercel → Settings → Domains
2. 添加你的域名（如 `mindmap.yourdomain.com`）
3. 按提示去域名商加一条 CNAME 记录
