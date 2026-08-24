# mihomo-rules

自托管的 mihomo（Clash Meta）自定义规则集。

## 规则列表

| 文件                                     | 用途               | behavior |
| ---------------------------------------- | ------------------ | -------- |
| [`rules/direct.yaml`](rules/direct.yaml) | 直连（DIRECT）分流 | domain   |

## 使用方法

在 mihomo 配置文件中添加：

```yaml
rule-providers:
  my-direct:
    type: http
    behavior: domain
    format: yaml
    url: "https://raw.githubusercontent.com/eivgogo/mihomo-rules/main/rules/direct.yaml"
    path: ./rules/my-direct.yaml
    interval: 86400

rules:
  - RULE-SET,my-direct,DIRECT
```

> 国内网络拉取 GitHub raw 可能失败，可将 `url` 替换为加速镜像，例如：
> `https://ghproxy.net/https://raw.githubusercontent.com/eivgogo/mihomo-rules/main/rules/direct.yaml`

## 维护规则

直接编辑 `rules/direct.yaml` 的 `payload` 列表即可：

```yaml
payload:
  - "+.example.com" # example.com 及其所有子域名直连
  - "example.org" # 仅精确匹配 example.org
```

提交并推送到 `main` 分支后，客户端会在 `interval` 到期时自动更新。
