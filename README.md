# 林致佑 · Zhi-Iu Lin — Personal Portfolio

個人介紹網站，使用 Docker + Nginx 架設。

---

## 📁 專案結構

```
portfolio/
├── index.html
├── Dockerfile
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

---

## 常用指令

```bash
docker stop portfolio       # 停止
docker start portfolio      # 重新啟動
docker rm portfolio         # 刪除 container
docker rmi portfolio        # 刪除 image
```
