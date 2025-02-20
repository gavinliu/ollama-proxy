# ollama-proxy

这是一个 ollama 的透明代理，可在 `./nginx/log/access_json.log` 中看到 AI 工具和大模型的详细交互过程

## 使用

1. 修改 `/nginx/conf/conf.d/default.conf` 中 `proxy_pass` 为你期望代理的服务地址

2. 启动代理

```
 docker run \
    -p 9002:80 \
    --name ollama-proxy \
    -v ./nginx/conf/nginx.conf:/etc/nginx/nginx.conf \
    -v ./nginx/conf/conf.d:/etc/nginx/conf.d \
    -v ./nginx/log:/var/log/nginx \
    -d nginx:latest
```

3. 在 AI 工具中使用 `ip:9002` 为 AI 服务
