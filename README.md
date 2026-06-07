# English Talk Trainer

AI-Powered English Conversation Practice PWA

Gemini 3.1 Flash-Lite / 3.5 Flash / 2.5 Pro × Azure Speech × PWA

## Features

### 4 Training Modes + Auto Routine
- **Free Talk** — AI英会話（17カテゴリ・221トピック・68ロールプレイ）。ターン数選択(3/5/7/10/∞)。自分スタートオプション。最終ターンでAIが自然に会話を締める。AIは質問だけでなく共感・リアクション・エピソードを自然に混ぜる
- **Flash Translation** — 瞬間英作文（7カテゴリ×5レベル）。⚡状況反応、🔄パターンドリル、🎨描写トレーニング含む
- **Shadowing** — AI発話を繰り返し＋Azure発音評価。単語ごと色分け。テキスト非表示モード。自分の録音再生。AIアドバイス（オプション有料）。最低スコアリトライ
- **News Discussion** — 実際のニュースを読んで議論（22ジャンル・Google Search Grounding）
- **🚀 自動ルーティン** — テーマ選択(12種) → Free Talk 3ターン → Flash 10問 → Shadowing 5文を自動連続。テーマが全セクションで統一

### Geminiモデル（4種対応）
- `gemini-3.1-flash-lite`（デフォルト・GA版・最速・無料枠あり）
- `gemini-2.5-flash`（安定版）
- `gemini-3.5-flash`（最高性能Flash・無料枠あり）
- `gemini-2.5-pro`（高精度）
- 廃止モデルの自動マイグレーション＋不正モデルID自動リセット

### CEFR 5段階レベルシステム（A1〜C1）
- 各レベルで語彙数・文法範囲（BANNEDリスト付き）・文の長さ・AI振る舞い・Good/BAD例文を体系定義
- TTS速度はレベルに関わらず全て自然速度
- AIの会話スタイル: 毎回質問で返さず、共感・自分の話・リアクションを自然に混ぜる

### 多様性システム
- Flash: 6カテゴリ×30シード + 文体10種 = 40,600+通り
- Shadowing: 30トピック×8スタイル = 32,480+通り
- 描写: 20テーマ×15場面×10展開 = 3,000+通り
- ルーティン時はFree Talkテーマに統一

### 学習支援
- **チャレンジ表現** — 22スキルカテゴリ×CEFR別。会話トピックに合った実用的フレーズ(2-6語)を生成
- **復習システム** — 間隔反復(0→1→3→7→14→30日)。フラッシュカード方式。🔊発音再生付き
- **フレーズ集** — 自動抽出。🔊フレーズ再生。✨例文＋🏷️使用シーン生成（有料）。個別削除
- **会話ログ** — 最大50件。🇯🇵和訳表示（番号付き1対1対応・有料）
- **⚡応答時間計測** — フィードバック画面に平均応答秒数
- **ストリーク+カレンダー** + **累計APIコスト表示**

### 音声
- **TTS**: Azure Neural TTS（10声×4アクセント）+ ブラウザ音声フォールバック
- **STT**: Azure STT / Web Speech API / 自動切替
- **発音評価**: Azure Pronunciation Assessment + EnableMiscue
- **マイクボタン**: 3状態CSS（idle/recording/processing）即座フィードバック

### コスト目安
- 3.1 Flash-Lite + Azure STT: 1回約5円（月約300円）
- Web Speech + 3.1 Flash-Lite: 1回約2.5円（月約150円）

## Setup

### Required
- **Gemini API Key** — [Google AI Studio](https://aistudio.google.com/apikey)

### Recommended
- **Azure Speech Key** — [Azure Portal](https://portal.azure.com/) → Speech Services

### Deployment
GitHub Pages等のHTTPS環境に配置。

```
English-Talk-Trainer/
├── index.html          # メインアプリ（単一ファイルSPA・3500行超）
├── sw.js               # Service Worker
├── manifest.json       # PWA マニフェスト
├── manual.html         # マニュアル
└── icon-*.png          # PWA アイコン
```

## Version
v2026.06.07a
