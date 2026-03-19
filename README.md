# 林致佑 · Zhi-Iu Lin — Personal Portfolio

個人介紹網站，使用 Docker + Nginx 架設，並透過 GitHub Actions 自動部署。

---

## 📁 專案結構

```
portfolio/
├── index.html
├── Dockerfile
├── .github/
│   └── workflows/
│       └── deploy.yml
└── README.md
```

---

## 🚀 本地啟動 Local

```bash
# Build image
docker build -t portfolio .

# Run（port 8080）
docker run -d -p 8080:80 --name portfolio portfolio
```

開啟瀏覽器 → http://localhost:8080

### 常用指令

```bash
docker stop portfolio       # 停止
docker start portfolio      # 重新啟動
docker rm portfolio         # 刪除 container
docker rmi portfolio        # 刪除 image
```

---

## ☁️ 部署到伺服器 Server Deploy

先確保伺服器有安裝 Docker，然後：

```bash
# 從 Docker Hub 拉取最新 image
docker pull 你的DockerHub帳號/portfolio:latest

# 啟動
docker run -d -p 80:80 --name portfolio 你的DockerHub帳號/portfolio:latest
```

### 更新網站

每次 push 到 GitHub main branch，GitHub Actions 會自動 build 並推到 Docker Hub。
在伺服器上執行：

```bash
docker stop portfolio && docker rm portfolio
docker pull 你的DockerHub帳號/portfolio:latest
docker run -d -p 80:80 --name portfolio 你的DockerHub帳號/portfolio:latest
```

---

## ⚙️ GitHub Actions 設定

需要在 GitHub repo 的 **Settings → Secrets and variables → Actions** 新增兩個 Secret：

| Secret 名稱 | 說明 |
|---|---|
| `DOCKERHUB_USERNAME` | 你的 Docker Hub 帳號名稱 |
| `DOCKERHUB_TOKEN` | Docker Hub 的 Access Token（不是密碼）|

### 取得 Docker Hub Token

1. 登入 [hub.docker.com](https://hub.docker.com)
2. 右上角頭像 → **Account Settings**
3. **Security** → **New Access Token**
4. 複製 token 貼到 GitHub Secret
