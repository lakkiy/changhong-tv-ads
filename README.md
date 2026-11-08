# 长虹电视去开屏广告（mihomo 规则）

用 mihomo 拦截长虹电视拉取和上报开屏广告的域名。

## 文件

- `rules-snippet.yaml`：直接粘到 mihomo 配置 `rules:` 最前面的规则。
- `changhong-tv-ads.yaml`：同样的域名，做成 rule-provider 格式，想用 `RULE-SET` 引用时用这个：

  ```yaml
  rule-providers:
    ChanghongTVAds:
      type: file
      behavior: classical
      path: ./rules/changhong-tv-ads.yaml
  rules:
    - RULE-SET, ChanghongTVAds, REJECT   # 放在最前面
  ```

规则要放在国内直连类规则集之前，否则这些域名会先被当作国内网站直连放行。

## 没有拦截的域名（电视正常功能要用）

`apilauncher.smart-tv.cn`（桌面）、`rs.smart-tv.cn`、`config.chsmarttv.com`、`app-upgrade.smart-tv.cn`（升级）、
`*.appstore.huan.tv` / `dl-appstore.cedock.com`（应用商店）、`api.weather.huan.tv`（天气）、`*.hpplay.cn` / `*.lebo.com.cn`（投屏）。

如果电视哪个功能坏了，先注释掉上面的规则逐条排查。
