# GeoIP 发布数据

本分支用于保存 GeoIP 数据文件。当前自定义构建流程更新以下文件及其 SHA256 校验文件：

- `Country-only-cn-private.mmdb`
- `geoip-only-cn-private.dat`
- `cn.dat`（仅包含 `cn`，不包含 `private`）
- `Country-only-cn-private.mmdb.sha256sum`
- `geoip-only-cn-private.dat.sha256sum`
- `cn.dat.sha256sum`

## 当前数据源

上述 `cn` 和 `private` 两个分类使用以下数据源直接生成：

### `cn`

唯一数据源为：

https://raw.githubusercontent.com/PaPerseller/chn-iplist/master/chnroute.txt

该文件已经是处理完成的中国大陆 IPv4/IPv6 CIDR 列表。构建时不会再加入 GeoLite2、MaxMind、China Operator、ASN、Cloudflare 或其他外部数据源，也不执行额外的数据源合并。

### `private`

`private` 分类使用项目源码内置的固定 CIDR 列表：

<https://github.com/PaPerseller/geoip/blob/master/plugin/special/private.go>

### `cn.dat`

`cn.dat` 只使用上述 `chnroute.txt` 数据源，仅包含 `cn` 分类，不包含项目内置的 `private` 列表。该文件为 V2Ray GeoIP DAT 格式，适用于只需要中国大陆 IP 数据、不需要内网和保留地址数据的场景。
