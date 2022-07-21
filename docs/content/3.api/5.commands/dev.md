# `nuxi dev`

```{bash}
npx nuxi dev [rootDir] [--clipboard] [--open, -o] [--no-clear] [--port, -p] [--host, -h] [--https] [--ssl-cert] [--ssl-key]
```

`dev` 命令会以热更新模式开启一个开发服务器默认地址时[http://localhost:3000](https://localhost:3000)

Option        | Default          | 描述
-------------------------|-----------------|------------------
`rootDir` | `.` | 要服务的应用程序的目录.
`--clipboard` | `false` | 把链接复制到剪贴板.
`--open, -o` | `false` | 打开浏览器.
`--no-clear` | `false` | 启动后不清除控制台.
`--port, -p` | `3000` | 监听的端口.
`--host, -h` | `localhost` | 服务器主机名.
`--https` | `false` | 开启HTTPS协议，默认使用自带的签名证书。
`--ssl-cert` |`null` | 指定https的证书.
`--ssl-key` |`null` | 指定https的证书密钥.

短裤和主机名也使用通过环境变量NUXT_PORT, PORT, NUXT_HOST 或 HOST来设置

此命令设置 `process.env.NODE_ENV` 为 `development`
