# Changelog — English Talk Trainer

## v2026.05.06s (2026-05-06)
- フレーズ集: 個別削除（✕ボタン）
- フレーズ集: Geminiで例文自動生成（✨ボタン）
- フレーズ集: Web Speech APIで例文音声再生（🔊ボタン）
- deleteVocabEntry / updateVocabEntry 関数追加

## v2026.05.06r (2026-05-06)
- speakBrowser話速をShadowingモード対応（currentLevel判定）
- startFreeTalkSession / handleUserMessage の catch側に sessionId ガード追加
- WAVヘッダーのサンプルレートを ctx.sampleRate 実測値に変更

## v2026.05.06q (2026-05-06)
- recordWav maxMs=0 の falsy バグ修正（`||` → `=== undefined || === null`）
- AudioContext シングルトン再利用（getAudioContext）、ctx.close()削除
- saveSession を safeLSSet で統一
- 戻るボタン: confirm前にリソース停止しない設計に修正

## v2026.05.06p (2026-05-06)
### Re-review Fixes (7 items)
- srCancel() 新設: 画面離脱時は結果を破棄（srStopと分離）
- endFreeTalkSession に ftEnding 二重実行防止
- startFreeTalkSession / handleUserMessage に ftSessionId ガード
- Shadowing recordWav(0) で自動停止なし
- Azure TTS失敗時もブラウザTTSフォールバック（speakBrowser）
- safeLSSet 容量超過時にalert通知（1セッション1回）
- recordWav にゼロゲインノード追加（エコー防止）

## v2026.05.06o (2026-05-06)
### Code Review Fixes (18 items)
#### 🔴 Critical (6)
- `abort()` → `stop()` + `onend`待ちに変更（音声認識されない主原因を修正）
- `recordWav` 自動停止で `onAutoStop` コールバック追加（結果消失を防止）
- `endFreeTalkSession()` を `await` 対応（画面遷移の競合修正）
- TTS失敗時にUIで「🔇 音声再生に失敗しました」と表示
- Streak日付をUTC → `localDateKey()` でローカル日付基準に
- XMLエスケープに `&apos;` 追加（I'm, don't等のSSMLエラー防止）

#### 🟡 Stability (6)
- `ftSessionId` で画面遷移後の非同期戻り防止
- `fetchT()` でAPI呼出にタイムアウト（Gemini 60秒、その他30秒）
- `safeLSSet()` で localStorage容量超過ガード
- APIキー空入力で `removeItem` 削除
- Geminiエラー詳細表示（レスポンスbody先頭200文字）
- マイクストリーム再利用（`getMicStream`/`releaseMicStream`）

#### 🟢 Quality (6)
- Azure未設定時のブラウザTTSフォールバック
- `@import` を `<link>` タグに移動
- ピンチズーム禁止解除
- 会話ログ容量制限（最新20件・各500文字）
- STTと発音評価のコスト分離（`pronSeconds`）
- 重複class属性修正

## v2026.05.06l (2026-05-06)
- CEFR `feedbackCriteria` をフィードバックプロンプトに復元
- `maxOutputTokens` 8192のコスト影響なし（実際の生成量で課金）
- 会話開始バリエーション 6 → 24パターンに拡充

## v2026.05.06k (2026-05-06)
- 単語帳 → フレーズ集に変更（ユーザー発言から抽出）
- HOME画面に累計APIコスト表示
- チャレンジ表現: Quick=1つ、通常=2つに調整
- AI開始バリエーション追加（6パターン）

## v2026.05.06j (2026-05-06)
- ターンインジケーター追加（🔊AI発話中 / 🎤あなたのターン）
- AI発話中は入力・マイク無効化
- フィードバックプロンプト簡素化（JSON切れ防止）
- `maxOutputTokens` 4096 → 8192

## v2026.05.06i (2026-05-06)
- デフォルト音声認識を Azure STT に変更

## v2026.05.06h (2026-05-06)
- `interimResults: true` のAndroid重複問題を修正（falseに戻す）

## v2026.05.06g (2026-05-06)
- マイクボタン 58→64px に拡大
- Azure STT dictation モード + detailed format
- リアルタイム文字表示（赤帯）

## v2026.05.06f (2026-05-06)
- 音声認識方式の設定追加（自動/Web Speech/Azure STT）
- `srMode` を localStorage に保存

## v2026.05.06e (2026-05-06)
- Geminiモデル切替（2.5 Flash / 2.5 Pro）
- モデル別コスト計算
- HOME画面にモデル名表示

## v2026.05.06d (2026-05-06)
- 音声認識エラーに3段階フォールバック（リトライ2回 → Azure）
- 旧インスタンス完全クリーンアップ

## v2026.05.06c (2026-05-06)
- Web Speech API → Azure STT 自動フォールバック機構
- PWAモード対応

## v2026.05.06b (2026-05-06)
- Speech モジュールをクロージャベースに全面書き直し
- `this` バインディング問題を解消
- recordWav を Shadowing専用に簡素化

## v2026.05.05r (2026-05-05)
- ニュースジャンル 8 → 22に拡充

## v2026.05.05q (2026-05-05)
- ニュースを Gemini Google Search Grounding で実際のニュースに変更
- 検索コスト追跡

## v2026.05.05p (2026-05-05)
- 📰 ニュース議論モード追加（Google Search Grounding）
- ニュース専用システムプロンプト

## v2026.05.05o (2026-05-05)
- 🎭 ロールプレイ 24 → 54に拡充（+30種）
- 全カテゴリに実用的なロールプレイ追加

## v2026.05.05n (2026-05-05)
- シチュエーションカテゴリ廃止、全トピックを各カテゴリに統合
- 🎭マーク付きで識別、`topic.id.startsWith("si_")` で判定

## v2026.05.05m (2026-05-05)
- 新カテゴリ追加: 健康・医療 / 家族・子育て / 住まい / ファッション / 自然・季節
- 17カテゴリ・155トピック

## v2026.05.05l (2026-05-05)
- ビジネストピック 8 → 19に拡充
- 💹 経済・金融カテゴリ新設（11トピック）
- ✏️ フリーワード入力を全カテゴリに追加

## v2026.05.05k (2026-05-05)
- チャレンジ表現をCEFRスキルカテゴリ体系に刷新（22カテゴリ×5レベル）
- ローテーション機能（直近20回の使用履歴管理）
- トピック連動の表現生成

## v2026.05.05j (2026-05-05)
- チャレンジ表現のAI評価をフィードバックに追加（✅使用/⚠️不自然/❌未使用）

## v2026.05.05i (2026-05-05)
- チャレンジ表現カード表示を大幅改善（紫カード・英語太字・日本語訳・例文）

## v2026.05.05h (2026-05-05)
- チャレンジ表現をトピック連動に変更

## v2026.05.05g (2026-05-05)
- Web Speech API `continuous: true` に変更

## v2026.05.05f (2026-05-05)
- 音声認識を Web Speech API（無料）に切替
- コスト表示更新（音声認識が「無料」表示）

## v2026.05.05e (2026-05-05)
- `maxOutputTokens` 2048 → 4096
- `safeJSON()` 自動修復機能追加

## v2026.05.05d (2026-05-05)
- HOME画面ヘッダーにバージョン表示

## v2026.05.05c (2026-05-05)
- SW強制更新機能（バージョン不一致時キャッシュクリア+リロード）

## v2026.05.05b (2026-05-05)
- CSS配置修正（`</style>`の外に出ていた問題）

## v2026.05.05a (2026-05-05)
### Major Feature Release
- 🎧 Shadowing モード追加
- 📝 復習システム（間隔反復）
- 🎯 チャレンジ表現
- 📅 ストリーク＋カレンダー
- 📚 単語帳（後にフレーズ集に変更）
- 💬 会話ログ
- ⚡ クイックモード（3ターン）
- 🔴 録音波形表示
- 🎯 自動CEFRレベル判定

## v2026.05.04j (2026-05-04)
- 初期安定版
- Free Talk + Flash Translation
- Azure TTS/STT
- CEFR 5段階レベル
- 10声×4アクセント自動選択
- コスト概算表示
- PWA対応
