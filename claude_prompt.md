# Claude Code への指示 - smarticket 残り画面実装

## 作業ディレクトリ
```
/Users/matsu/Desktop/smarticket/
```

## 現状
`index.html`（132行）にチケット詳細画面（DetailView）は完成している。
SelectionViewはプレースホルダーのみ。

## 参考画像（必ず全部確認すること）
```
/Users/matsu/.openclaw/media/inbound/file_37---cf3cc05b-f42b-4974-a4b4-1aa7c8d6d348.jpg  # 本物・未使用状態
/Users/matsu/.openclaw/media/inbound/file_36---31a37cf5-c723-4ef5-a56c-a26bf49757fb.jpg  # 本物・使用済み状態
/Users/matsu/.openclaw/media/inbound/file_38---f6724b68-f08c-425c-a657-f4856ef885fb.jpg  # 現在の実装
/Users/matsu/.openclaw/workspace/vid_05s.jpg   # GATE画面（スライダー前）
/Users/matsu/.openclaw/workspace/vid_10s.jpg   # GATE画面（スライダー操作中）
/Users/matsu/.openclaw/workspace/vid_14s.jpg   # 使用済み確認画面
```

## やること

### 1. SelectionView を本物のGATE入場画面に作り直す
参考画像 `vid_05s.jpg` / `vid_10s.jpg` を見て以下を実装：

- **背景**: 黒 or 暗めのグラデーション
- **上部**: ミリ秒まで表示するタイムスタンプ（リアルタイム更新）
- **中央**: ★（星）が複数点滅するアニメーション
- **入場ゲート名**（GATE A / GATE B 等）を表示
- **スライダー**: 桜アイコン🌸を右にドラッグ → 右端まで到達したら UsedView へ遷移
  - ドラッグ中はスライダーが追従
  - 右端まで行ったら `setCurrentView('used')` を呼ぶ
- e+のカラー（#E91E8C）を使用

### 2. UsedView を新規追加する
参考画像 `vid_14s.jpg` / `file_36...jpg` を見て以下を実装：

- **「使用済み」確認画面**: 使用した時刻・ゲート名を表示
- **×ボタン**: 押すと DetailView に戻り、チケットが「使用済み」状態に変化
- 使用済み状態のDetailViewでは「未使用」バッジを「入場済」（グレー背景・白文字）に変更

### 3. DetailView の「入場画面に進む」ボタン修正
現在 `setCurrentView('selection')` になっているがそのまま（GATEへ遷移）でOK

### 4. URLパラメーター対応（任意だが可能なら）
- `?name=東久保慶樹&event=イープラス劇団...` でチケット情報を動的に変更できるようにする

## 技術制約
- **1ファイル完結**（index.html のみ）
- React 18 + Tailwind CDN + Babel standalone（現在の構成を維持）
- max-width: 390px（スマホ幅）
- GitHub Pages で動作（静的HTML）

## 完了条件
実装完了後：
```bash
git add -A && git commit -m "feat: GATE animation and used screen" && git push
echo "===COMPLETE==="
```

## 注意
- 参考画像をピクセルレベルで見て、色・フォント・余白を本物に近づける
- スライダーはtouchイベントとmouseイベント両方対応（スマホで動くこと）
- 現在のDetailViewのコードは壊さないこと
