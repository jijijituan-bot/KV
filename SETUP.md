# KVideo 影视资源配置说明

## 已配置的资源

本项目已经配置了来自 `https://raw.githubusercontent.com/rapier15sapper/ew/refs/heads/main/test.json` 的影视资源订阅源。

该订阅源包含了 **78 个视频资源站点**，分为两类：

### 普通资源（56个）
包括：非凡资源、卧龙资源、最大资源、百度云资源、暴风资源、极速资源等主流影视资源站。

### 高级资源（22个）
包括：乐播资源、CK、jkun、155、lsb等特殊内容资源站。

## 快速启动

### 1. 安装依赖
```bash
npm install
```

### 2. 启动开发服务器
```bash
npm run dev
```

应用将在 `http://localhost:3000` 启动。

### 3. 构建生产版本
```bash
npm run build
npm start
```

## 环境变量配置

项目已经在 `.env.local` 文件中配置了订阅源。你可以根据需要修改以下配置：

### 订阅源配置
```bash
SUBSCRIPTION_SOURCES='[{"name":"影视资源集合","url":"https://raw.githubusercontent.com/rapier15sapper/ew/refs/heads/main/test.json"}]'
```

### 访问控制（可选）
如果需要设置访问密码，取消注释并设置：
```bash
ADMIN_PASSWORD=your_password_here
PREMIUM_PASSWORD=premium_password_here
```

### 站点自定义（可选）
```bash
NEXT_PUBLIC_SITE_NAME=我的视频平台
NEXT_PUBLIC_SITE_TITLE=我的视频 - 聚合播放平台
NEXT_PUBLIC_SITE_DESCRIPTION=专属视频聚合播放平台
```

## Docker 部署

如果你想使用 Docker 部署，可以使用以下命令：

```bash
docker build -t kvideo .
docker run -d -p 3000:3000 \
  -e SUBSCRIPTION_SOURCES='[{"name":"影视资源集合","url":"https://raw.githubusercontent.com/rapier15sapper/ew/refs/heads/main/test.json"}]' \
  --name kvideo kvideo
```

或者使用 Docker Hub 镜像：

```bash
docker pull kuekhaoyang/kvideo:latest
docker run -d -p 3000:3000 \
  -e SUBSCRIPTION_SOURCES='[{"name":"影视资源集合","url":"https://raw.githubusercontent.com/rapier15sapper/ew/refs/heads/main/test.json"}]' \
  --name kvideo kuekhaoyang/kvideo:latest
```

## 功能说明

### 自动加载资源
应用启动时会自动从配置的订阅源加载所有视频资源站点，无需手动添加。

### 搜索功能
- 在首页搜索框输入影视名称
- 系统会并行搜索所有已配置的资源站
- 实时显示搜索结果

### 高级内容
- 访问 `/premium` 路径可以查看高级内容资源
- 如果设置了 `PREMIUM_PASSWORD`，需要输入密码才能访问

### 资源管理
- 在设置页面可以查看和管理所有视频源
- 支持启用/禁用特定资源站
- 支持调整资源站优先级

## 资源更新

订阅源会自动更新。如果源文件 `test.json` 有更新，应用会自动获取最新的资源列表。

你也可以在设置页面手动触发更新。

## 故障排除

### 资源无法加载
1. 检查网络连接
2. 确认订阅源 URL 可以访问
3. 查看浏览器控制台是否有错误信息

### 视频无法播放
1. 尝试切换其他资源站的线路
2. 检查视频源是否可用
3. 某些资源可能需要代理访问

## 更多信息

详细的功能说明和配置选项请参考主 [README.md](README.md) 文件。
