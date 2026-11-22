# FreeToken-Bots

Scan OpenRouter for currently free models and write a local report for Pi child-agent workflows.

掃描 OpenRouter 目前的免費模型，並把結果寫成本機報告，供 Pi 子代理流程使用。

## 執行掃描

在本技能目錄執行：

```bash
python3 scripts/radar.py scan
```

其他指令：

- `python3 scripts/radar.py status`：讀取上次掃描報告
- `python3 scripts/radar.py probe --model '<精確模型 ID>'`：探測單一已確認的免費模型
- `python3 scripts/radar.py sync --dry-run`：只產生建議，不會改 Pi 設定

此技能只用 Python 標準函式庫，不需另外安裝套件。

## 環境變數（只寫名稱，不要把值放進檔案或 Git）

- `OPENROUTER_API_KEY`：只有 `probe` 需要。`scan` 與 `status` 不需要此變數。

## 輸出

- 標準輸出：JSON 報告，內容包含掃描時間、免費模型清單 `free_ids`、合格名單 `eligible`，以及待確認參數量的 `needs_parameter_verification`。
- 本機快取檔（權限 600）：`~/.pi/agent/freetoken-bots.json`
- 若有設定每日排程比對：歷史檔會寫到 `~/.pi/agent/freetoken-history/`（不在本 repo 內）

免費資格會變動，建議每天跑一次 `scan`。詳細規則見 `SKILL.md`。
