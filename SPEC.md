# smarticket - 修正仕様書

## ゴール
index.htmlをe+スマートチケットの本物と瓜二つにする。
参考画像を直接見て、ピクセルレベルで忠実に再現すること。

## 参考画像（必ず全部見ること）
- 本物・未使用状態: /Users/matsu/.openclaw/media/inbound/file_37---cf3cc05b-f42b-4974-a4b4-1aa7c8d6d348.jpg
- 本物・使用済み状態: /Users/matsu/.openclaw/media/inbound/file_36---31a37cf5-c723-4ef5-a56c-a26bf49757fb.jpg
- 私の実装（現状）: /Users/matsu/.openclaw/media/inbound/file_38---f6724b68-f08c-425c-a657-f4856ef885fb.jpg
- 動画フレーム(GATE画面1): /Users/matsu/.openclaw/workspace/vid_05s.jpg
- 動画フレーム(GATE画面2): /Users/matsu/.openclaw/workspace/vid_10s.jpg
- 動画フレーム(使用済み): /Users/matsu/.openclaw/workspace/vid_14s.jpg

## 現在の問題点（参考画像と比較して修正すること）
画像を見て本物との差分を全て特定し、完璧に再現すること。

## 技術要件
- 1ファイル(index.html)完結
- URLパラメーター対応（name/event/venue/date/day/open/start/type/floor/row/num/price/ticket_num）
- GitHub Pagesで動作（静的）
- スマートフォン幅 max-width:390px
- フォント: -apple-system, "Hiragino Sans", sans-serif

## 画面構成
1. チケット詳細画面（メイン）
2. GATE入場画面（ミリ秒タイムスタンプ・★点滅・スライダー）
3. 使用済み確認画面（スライド完了後）
→ ×で閉じると画面1が使用済み状態に変化

## 完了後
git add -A && git commit -m "feat: Perfect e+ smarticket clone via Claude Code" && git push
echo "===COMPLETE==="
