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

