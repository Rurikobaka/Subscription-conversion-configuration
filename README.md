# 訂閱轉換模板

模板來自 `ACL4SSR`，規則基於 `blackmatrix7`,`hope140`,`dler-io`,`sstap-rules`,`LM-Firefly` 以及我的朋友，感謝！

## Rules

此資料夾下為我特殊需要無法直接使用上述規則來源的規則集，所以進行了一些修改方便使用，以及我自己來源維護的一些規則

#### 規則說明：

```
:D.yaml                     —————>>> MIUI 阻止更新規則，需設定為 REJECT （幫朋友製作）
ChatGPT.yaml                —————>>> ChatGPT 規則，來源於 dler-io
Crisp.yaml                  —————>>> Crisp 規則 
Diablo 2 Resurrected.yaml   —————>>> 暗黑破壞神 2 重製版規則，來源於 sstap-rules
Diablo IV.yaml              —————>>> 暗黑破壞神 4 規則，永生不朽規則，同時包含流亡黯道、暴雪英霸，來源於朋友，應該是目前比較全面的規則了
Diablo IV.list              —————>>> 暗黑破壞神 4 規則，不過是 Surge 版本
Diablo Immortal.yaml        —————>>> 暗黑破壞神 永生不朽規則
Path Of Exile.yaml          —————>>> 流亡黯道規則，來自 sstap-rules （和上面的 Diablo IV.yaml 規則類型不同，有點懶得改了）
Steam Download.yaml         —————>>> Steam 下載遊戲的規則，建議設定為 DIRECT，來源於 blackmatrix7
WorldofWarcraft.yaml        —————>>> 魔獸世界規則，部分來源於 blackmatrix7，部分來源於朋友補全，應該是目前比較全面的規則了
apk.yaml                    —————>>> APKPure 和 APKMirror，部分來自於 blackmatrix7
gov.yaml                    —————>>> 常見的 GOV 規則，某些代理審計 GOV，設定為 DIRECT 就可以直連訪問；或者設定為 REJECT 禁止訪問 GOV
WiFiCalling.list            —————>>> WiFi 通話相關規則
```
```
DNS.stoverride              —————>>> 自用 Stash 複寫，和 ClashConfig.yml 內容一致
```

## 主倉庫

#### `rurikocustom.yaml`  全面規則，如果不是很清楚各個策略組作用建議使用 `rurikocustomlite.yaml`

幾個特殊需要說明的策略組

```
Domestic         —————>>> 大陸內地 IP
Others           —————>>> Proxy 的遺漏補全
CloudFlare       —————>>> 建議 DIRECT，防止使用代理 IP 遭到網站 CloudFlare 防禦阻止，但在某些情況下，設定為代理可以加速訪問
Google           —————>>> 包含所有 Google 服務，包含 FCM 
Steam Download   —————>>> 建議設定為 DIRECT，以達到社區、商店可以通過代理訪問，而下載不耗費代理流量的目的
Game             —————>>> 除了 Steam 其他遊戲平台的遊戲下載均會命中此策略組規則
```

#### `rurikocustomlite.yaml`  精簡版規則，策略組數量極少，適合日常使用

幾個特殊需要說明的策略組

```
CloudFlare       —————>>> 建議 DIRECT，防止使用代理 IP 遭到網站 CloudFlare 防禦阻止，但在某些情況下，設定為代理可以加速訪問
Google           —————>>> 包含所有 Google 服務，包含 FCM ，但是 YouTube 應該是命中 Global TV 策略組規則
Steam Download   —————>>> 建議設定為 DIRECT，以達到社區、商店可以通過代理訪問，而下載不耗費代理流量的目的
Game             —————>>> 除了 Steam 其他遊戲平台的遊戲下載均會命中此策略組規則
```

`rurikocustom.yaml` 中的 `Domestic` 預設為 `DIRECT`，`Others` 預設為 `Proxy`，`Adblock` 預設為 `REJECT`，且無法修改，一般來說也不需要進行修改，方便使用

#### `TikTok.yaml`

在 `rurikocustomlite.yaml` 的基礎上新增了 `TikTok` 策略組，用於訪問各個地區的 TikTok

#### `:D.yaml`

朋友定製，基於 `rurikocustomlite.yaml` 修改

```
· 新增 MIUI 更新規則並預設為 REJECT 
· 獨立出 bilibili 策略組，方便更換港澳台區域
· 獨立出 Twitter 策略組 
· 獨立出 Spotify 策略組 
```

#### `ClashConfig.yml`

使用我的訂閱轉換模板並且轉換為 `clash` 訂閱的 `端口` 以及 `DNS` 字段的配置

#### `ruriko_hw.yaml`

`rurikocustom.yaml`  全面規則對於 硬路由（CPU 性能超低的那種） 的優化版，去掉了大量不是很重要的規則，以減輕負擔
