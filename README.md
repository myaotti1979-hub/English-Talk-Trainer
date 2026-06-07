# English Talk Trainer

AI-Powered English Conversation Practice PWA

Gemini API × Azure Speech × PWA

## Features

### 5 Training Modes + Auto Routine
- **Free Talk** — AI英会話（17カテゴリ・221トピック・68ロールプレイ）。ターン数選択(3/5/7/10/∞)。自分スタートオプション。最終ターンでAIが自然に締める
- **Flash Training** — 瞬間英作文（6カテゴリ×5レベル）。⚡状況反応、🔄パターンドリル含む
- **Shadowing** — 発音評価＋単語色分け。テキスト非表示モード。録音再生。AIアドバイス（有料）。リトライ
- **Description** — シナリオベースの描写トレーニング。段階的5問。テーマ×場面×展開で3,000+通り
- **News Discussion** — 最新ニュースで議論（22ジャンル・Google Search Grounding）
- **🚀 自動ルーティン** — Free Talk 3ターン → Flash 5問 → Description 5問 → Shadowing 5文。テーマ統一（12種）

### Geminiモデル（4種）
- `gemini-3.1-flash-lite`（デフォルト・最速・無料枠）
- `gemini-2.5-flash` / `gemini-3.5-flash` / `gemini-2.5-pro`
- 廃止モデル自動マイグレーション + 不正ID自動リセット

### 学習支援
- CEFR 5段階（A1〜C1）。BANNEDリスト・Good/BAD例文付き
- チャレンジ表現（22スキル×CEFR別・実用フレーズ2-6語）
- 復習（間隔反復0→30日・フラッシュカード方式）
- フレーズ集（🔊再生・✨例文＋🏷️使用シーン生成）
- 会話ログ（🇯🇵和訳表示）
- ⚡応答時間計測 / ストリーク / 累計コスト表示

### 多様性システム
- Flash: 6カテゴリ×30シード + 文体10種 = 40,600+通り
- Shadowing: 30トピック×8スタイル = 32,480+通り
- Description: 20テーマ×15場面×10展開 = 3,000+通り

## Setup
- **Gemini API Key**（必須）— [Google AI Studio](https://aistudio.google.com/apikey)
- **Azure Speech Key**（推奨）— [Azure Portal](https://portal.azure.com/)

## Version
v2026.06.07e
