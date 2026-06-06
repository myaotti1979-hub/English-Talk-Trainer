# English Talk Trainer

AI-Powered English Conversation Practice PWA

Gemini 3.1 Flash-Lite / 3.5 Flash / 2.5 Pro × Azure Speech × PWA

## Features

### 4 Training Modes + Auto Routine
- **Free Talk** — AI英会話（17カテゴリ・221トピック・68ロールプレイ）。ターン数選択(3/5/7/10/∞)。自分スタートオプション。最終ターンでAIが自然に会話を締める
- **Flash Translation** — 瞬間英作文（6カテゴリ×5レベル）。⚡状況反応モード、🔄パターンドリル含む
- **Shadowing** — AI発話を繰り返し＋Azure発音評価。単語ごと色分け。テキスト非表示モード。自分の録音再生。AIアドバイス（オプション有料）。最低スコアリトライ
- **News Discussion** — 実際のニュースを読んで議論（22ジャンル・Google Search Grounding）
- **🚀 自動ルーティン** — テーマ選択(12種) → Free Talk 3ターン → Flash 10問 → Shadowing 5文を自動連続。テーマが全セクションで統一

### Geminiモデル（4種対応）
- `gemini-3.1-flash-lite`（デフォルト・GA版・最速・無料枠あり）
- `gemini-2.5-flash`（安定版）
- `gemini-3.5-flash`（最高性能Flash・無料枠あり）
- `gemini-2.5-pro`（高精度）
- 廃止モデルの自動マイグレーション対応

### CEFR 5段階レベルシステム（A1〜C1）
- 各レベルで語彙数・文法範囲（BANNEDリスト付き）・文の長さ・AI振る舞い・Good/BAD例文を体系定義
- TTS速度はレベルに関わらず全て自然速度
- AIの会話スタイル: 毎回質問で返さず、共感・自分の話・リアクションを自然に混ぜる

### 学習支援
- **チャレンジ表現** — 22スキルカテゴリ×CEFR別ローテーション。会話トピックに合った実用的フレーズを生成。未使用分は復習キューに自動追加
- **復習システム** — 間隔反復(0→1→3→7→14→30日)。シンプルフラッシュカード方式。🔊発音再生付き。タイプ別表示(Free Talk修正/Flash不正解/未使用チャレンジ)
- **フレーズ集** — ユーザー発言から自動抽出。個別削除(✕)、AI例文＋使用シーン生成(✨)、フレーズ・例文音声再生(🔊)
- **会話ログ** — 最大50件。🇯🇵和訳表示（オプション有料）で自分の英語が伝わっていたか確認
- **⚡応答時間計測** — ターン開始→発話完了の秒数をフィードバック画面に表示
- **ストリーク+カレンダー** — ローカル日付基準
- **累計APIコスト表示** — HOME画面にドル＋円換算

### 多様性システム
- 6カテゴリ×15テーマの「VARIETY_SEEDS」を毎回ランダム3つ選びプロンプトに注入
- Shadowingも15トピックからランダム3つで毎回異なる文を生成
- ルーティン時はFree Talkテーマに統一

### 音声
- **TTS**: Azure Neural TTS（10声×4アクセント）+ ブラウザ音声フォールバック
- **STT**: Azure STT（デフォルト）/ Web Speech API / 自動切替
- **発音評価**: Azure Pronunciation Assessment + EnableMiscue（未発話検出）
- **マイクボタン**: 3状態CSS（idle/recording/processing）で即座のフィードバック

### コスト最適化
- 3.1 Flash-Lite + Azure STT: 1セッション約5円
- Web Speech + 3.1 Flash-Lite: 1セッション約2.5円
- 有料オプション（AIアドバイス等）は明示ラベル付き
- 累計コストをホーム画面に表示

## Setup

### Required
- **Gemini API Key** — [Google AI Studio](https://aistudio.google.com/apikey)

### Recommended
- **Azure Speech Key** — [Azure Portal](https://portal.azure.com/) → Speech Services

### Deployment
GitHub Pages, Netlify, Cloudflare Pages 等のHTTPS環境に配置。

```
English-Talk-Trainer/
├── index.html          # メインアプリ（単一ファイルSPA）
├── sw.js               # Service Worker
├── manifest.json       # PWA マニフェスト
├── manual.html         # マニュアル
├── icon-192.png        # PWA アイコン
├── icon-512.png        # PWA アイコン（大）
└── apple-touch-icon-*.png  # iOS アイコン
```

## Tech Stack
- **AI**: Gemini 3.1 Flash-Lite / 3.5 Flash / 2.5 Pro（Google AI Studio API）
- **Speech**: Azure Cognitive Services Speech SDK
- **Frontend**: Vanilla HTML/CSS/JS（フレームワークなし・3500行超の単一HTML）
- **PWA**: Service Worker（network-first） + Web App Manifest

## Code Quality
- GPT-4o / Gemini によるダブルコードレビュー実施済み（計38件修正）
- 音声認識: srStop（結果返却）/ srCancel（結果破棄）の安全分離設計
- 非同期ガード: sessionId + ftEnding による二重実行防止
- AudioContext シングルトン再利用 + ゼロゲインノード
- Azure TTS → ブラウザTTS 自動フォールバック
- Service Worker強制更新（バージョン不一致→キャッシュ全削除）
- safeLSSet()で容量超過ガード
- 廃止モデル自動マイグレーション + 不正モデルID自動リセット

## Version
v2026.05.30g

## License
Private / Personal Use
