# KVideo 部署指南

## 🎉 部署问题已修复

所有 TypeScript 类型错误和构建问题已经解决，现在可以正常部署了！

## ✅ 已完成的配置

### 1. 影视资源配置
- ✅ **56个普通影视资源站点**（非凡资源、卧龙资源、最大资源等）
- ✅ **22个高级资源站点**（访问 `/premium` 路径可用）
- ✅ 所有资源已内置到代码中，无需额外配置

### 2. 类型安全修复
- ✅ 为所有 `VideoSource` 添加了必需的 `searchPath` 和 `detailPath` 属性
- ✅ TypeScript 编译通过
- ✅ 构建成功验证

### 3. 开发环境配置
- ✅ 修复了 package.json 中的端口配置
- ✅ 本地开发服务器正常启动

## 🚀 部署方式

### 方式一：Vercel 一键部署（推荐）
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/jijijituan-bot/KV.git)

1. 点击上方按钮
2. 连接你的 GitHub 账号
3. Vercel 会自动检测并部署
4. 几分钟后即可访问

### 方式二：Cloudflare Pages 部署
1. Fork 本仓库到你的 GitHub
2. 访问 [Cloudflare Pages](https://dash.cloudflare.com/?to=/:account/pages/new/provider/github)
3. 选择你的 KV 仓库
4. 构建设置：
   - **Framework Preset**: `Next.js`
   - **Build command**: `npm run pages:build`
   - **Build output directory**: `.vercel/output/static`
5. 点击 **Save and Deploy**

### 方式三：Docker 部署
```bash
# 使用预构建镜像
docker pull kuekhaoyang/kvideo:latest
docker run -d -p 3000:3000 --name kvideo kuekhaoyang/kvideo:latest

# 或者自己构建
git clone https://github.com/jijijituan-bot/KV.git
cd KV
docker build -t kvideo .
docker run -d -p 3000:3000 --name kvideo kvideo
```

### 方式四：传统 Node.js 部署
```bash
git clone https://github.com/jijijituan-bot/KV.git
cd KV
npm install
npm run build
npm start
```

## 🎯 功能验证

部署完成后，你可以：

1. **搜索测试**：在首页搜索任何影视名称（如"复仇者联盟"）
2. **普通资源**：主页面可以搜索到56个资源站的内容
3. **高级资源**：访问 `/premium` 路径查看22个高级资源站
4. **播放测试**：点击任意视频进入播放页面

## 🔧 可选配置

### 环境变量（可选）
如果需要自定义配置，可以设置以下环境变量：

```bash
# 访问控制
ADMIN_PASSWORD=your_password_here
PREMIUM_PASSWORD=premium_password_here

# 站点自定义
NEXT_PUBLIC_SITE_NAME=我的视频平台
NEXT_PUBLIC_SITE_TITLE=我的视频 - 聚合播放平台

# 订阅源（已内置，可选）
SUBSCRIPTION_SOURCES='[{"name":"影视资源集合","url":"https://raw.githubusercontent.com/rapier15sapper/ew/refs/heads/main/test.json"}]'
```

## 📱 访问地址

部署成功后：
- **主页面**：`https://your-domain.com/`
- **高级内容**：`https://your-domain.com/premium`
- **设置页面**：`https://your-domain.com/settings`
- **IPTV直播**：`https://your-domain.com/iptv`

## 🎊 恭喜！

你的 KVideo 影视聚合平台已经配置完成，包含78个视频资源站点，可以立即使用！

如有问题，请查看 [README.md](README.md) 获取更多详细信息。