# Tainan Mobility Atlas — 01 Traffic Safety

台南市交通安全地圖｜十年回顧（民 105–114 / 2016–2025）

互動式單頁地圖儀表板，以警政署 A1 級道路交通事故開放資料為基礎，視覺化呈現台南市十年的死亡事故空間分布、年度趨勢、熱力圖與優先治理路段。

## 線上預覽

GitHub Pages：`https://yunching0513.github.io/tainan-mobility-atlas/`

姊妹專案：[Taitung Mobility Atlas](https://github.com/yunching0513/taitung-mobility-atlas) — 同樣風格、同樣資料來源，台東縣版本。

## 內容概要

- **01 — Decade Overview**：1,785 人 / 1,745 件 / 2016–2025
- **02 — Year-over-Year**：年度趨勢折線、運具組成堆疊棒、行政區 × 年熱力圖、2025 年快照
- **03 — Spatial Distribution**：Leaflet 互動地圖（2018+ 有經緯度），支援
  - 年份 / 運具篩選
  - 點位 / 熱力 / 兩者 View 切換
  - 點圓點看完整事件明細
- **Top Hotspots**：以 ~3 公里路段聚合，列出優先治理的前 10 名路段
- **04 — Headline Finding**：機車佔 52% 的關鍵發現
- **05 — Breakdown**：行政區、運具、道路類別、光線、24 小時、12 月份切面
- **06 — Notes**：資料來源與年度欄位差異說明

## 主要觀察（十年累計）

- **死亡人數年均 ~179 人**；2020 年為高峰（194 人）
- **機車為主要事故方**佔 52%（910 / 1,745 件）
- **市區道路** 佔 52%（913 件）— 治理重點是聚落內部路網與市區交叉口，**不是**快速幹道
- 行政區累計死亡前五：**安南區 154、永康區 117、仁德區 96、新市區 70、麻豆區 69**

## 資料來源

- [內政部警政署 — A1 級交通事故公開資料](https://www.npa.gov.tw/)
- 透過 [政府資料開放平臺 data.gov.tw](https://data.gov.tw/) 取得，包含
  [歷史交通事故資料 (12197)](https://data.gov.tw/dataset/12197)、[A1 與 A2 (130110)](https://data.gov.tw/en/datasets/130110) 等

A1 定義：造成人員當場或 24 小時內死亡之道路交通事故。

## 資料欄位完整度

| 年度 | Schema | 經緯度 | 完整欄位（道路類別、肇因、光線等） |
|---|---|---|---|
| 2016 | 簡式 | ✗ | ✗ |
| 2017 | 簡式 | ✗ | ✗ |
| 2018–2020 | 完整 | ✓ | ✓ |
| 2021 | 簡式 | ✓ | ✗ |
| 2022–2025 | 完整 | ✓ | ✓ |

## 檔案

```
index.html                 # 主頁面（單檔含所有 CSS + UI + Leaflet + Leaflet.heat）
tainan_a1.js              # 事件級資料與年度彙整 (window.TAINAN_A1 / TAINAN_YEARLY)
extract_city.py            # 從原始 CSV 萃取的腳本（CSV 不附在 repo 中）
```

## 自行重跑

```bash
# 1. 從 data.gov.tw 下載 105–114 年 A1 CSV，放到 ./資料/<年>年傷亡道路交通事故資料/
# 2. 跑萃取腳本
python3 extract_city.py tainan
# 輸出寫到 build_tainan/，再複製到 repo 根目錄
```

## 設計

Vision Zero Taiwan (VZT) 視覺風格：
- Lime `#C8D400` 為唯一強調色
- Noto Sans TC + Space Grotesk 字體組合
- 大量留白、超細字重 (100–300) 對大字號的對比
- 圓環為核心幾何元素

地圖底圖：CARTO Positron。熱力圖：Leaflet.heat（lime → gold → red）。

## 開發者

吳昀慶 · Designed for 台南市交通安全分析

## 授權

程式碼：MIT。資料：依政府資料開放平臺授權條款，可自由使用，請註明來源。
