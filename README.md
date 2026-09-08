# English Talk Trainer

AI-Powered English Conversation Practice PWA

Gemini API × Azure Speech × PWA

## Features

### 7 Training Modes + Auto Routine
- **🗣️ Free Talk** — AI英会話（17カテゴリ・221トピック・68ロールプレイ）。ターン数選択(3/5/7/10/∞)。自分スタート。AIは質問だけでなく共感・自分の話・リアクションを混ぜる
- **⚡ Flash Training** — 瞬間英作文（6カテゴリ）。⚡状況反応、🔄パターンドリル含む。30シード×10文体で40,600+通り
- **🎨 Description** — シナリオ描写トレーニング。段階的5問（報告→叙述→説明→比較説得→即興対応）。テーマ×場面×展開で3,000+通り
- **🎧 Shadowing** — Azure発音評価。単語色分け・テキスト非表示・録音再生・最低スコアリトライ。レベル×非表示で正規化
- **👂 Listening Quiz** — 聞いてタップのみ。6タイプ（ミックス/穴埋め/意図・感情/弱形・短縮/次の一言/数字）。マイク不要で電車でも可
- **🔁 4/3/2 Fluency** — 同じ話を50→40→30秒で3回。朝のFree Talk話題を自動で引き継ぐ。WPM・フィラー率をローカル計測し、3回分を1回のAPI呼出で比較（内容/構成/表現/流暢さ）
- **📰 News Discussion** — 最新ニュースで議論（22ジャンル・Google Search Grounding）。レベル別記事長(A1:30語〜C1:180語)
- **🚀 自動ルーティン** — 12テーマ。Free Talk 3ターン → Flash 5問 → Description 5問 → Shadowing 5文。全セクションでレベル・テーマ統一

### Geminiモデル
| モデル | 入力/1M | 出力/1M | 用途 |
|---|---|---|---|
| `gemini-3.1-flash-lite` | $0.25 | $1.50 | デフォルト・最速最安 |
| `gemini-2.5-flash` | $0.30 | $2.50 | 安定版 |
| `gemini-3.7-flash` | $0.75 | $3.75 | 最高性能・**Description専用固定** |
| `gemini-2.5-pro` | $1.25 | $10.00 | 高精度 |

廃止モデルの自動マイグレーション + 不正モデルID自動リセット。Descriptionのみシナリオ品質のため3.7 Flash固定（コストは別カウンタで計上）。

### 学習支援
- **📝 復習** — 間隔反復(0→1→3→7→14→30日)。**能動想起方式**（手がかり→答えを見る→自己判定）
  - 入口6系統: Free Talk修正 / Flash不正解 / Listening誤答 / Description低スコア / 発音弱点語 / 未使用チャレンジ表現
- **🎯 発音練習** — Shadowingで不正確だった語を自動収集。ドリルで録音→Azure採点→70点で合格、80点×2回で卒業。出題は3方式（おまかせ/苦手順/ランダム）
- **📚 フレーズ集** — 自動抽出。🔊再生・✨例文＋🏷️使用シーン生成・個別削除
- **💬 会話ログ** — 最大50件。🇯🇵和訳（**保存されるので2回目以降は無料**）
- **チャレンジ表現** — 22スキル×CEFR別。未使用分は復習キューへ

### 📊 分析（独立画面）
- スキルバランス（モード別レーダー・2週間 vs 1ヶ月）
- 弱点分析（6軸: 発音/流暢さ/文法/語彙/自然さ/瞬発力）+ 自動アドバイス
- 🏷️ 間違いの傾向（時制/冠詞/前置詞/語順/語彙選択など10分類）
- 👂 リスニング分析（タイプ別・直近50問ローリング）
- スコア推移（日別・1ヶ月）/ 週別学習推移（8週）/ 🎓 CEFRレベル推移（13段階）

### 音声
- **TTS**: Azure Neural TTS（10声×4アクセント）→ ブラウザ音声フォールバック
- **STT**: Azure STT / Web Speech / 自動切替。セッション番号照合で結果の取り違えを防止
- **発音評価**: Azure Pronunciation Assessment + EnableMiscue
- 全Azure API呼出に429自動リトライ（3秒→6秒→9秒）

### データ管理
📤 保存 / 📥 復元（JSON・全17項目）でスマホ交換時のデータ移行に対応。

### コスト目安
| 構成 | 1回 | 月額(朝晩) |
|---|---|---|
| 3.1 Flash-Lite + Azure STT | 約5円 | 約300円 |
| 3.1 Flash-Lite + Web Speech | 約2.5円 | 約150円 |

## Setup
- **Gemini API Key**（必須）— [Google AI Studio](https://aistudio.google.com/apikey)
- **Azure Speech Key**（推奨）— [Azure Portal](https://portal.azure.com/)

## Files
```
index.html      # 単一ファイルSPA（5,000行超）
sw.js           # Service Worker
manifest.json   # PWA マニフェスト
manual.html     # アプリ内マニュアル
icon-*.png      # PWA アイコン
```

## Version
v2026.09.08b
