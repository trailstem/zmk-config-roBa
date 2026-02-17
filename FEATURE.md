# roBa カスタム設定（GUIで設定不可）

## トラックボール速度 (boards/shields/roBa/roBa_R.conf)

- CONFIG_PMW3610_CPI = 2000 / CONFIG_PMW3610_CPI_DIVIDOR = 2（実効CPI 1000、センサー高解像度モード）
- CONFIG_PMW3610_POLLING_RATE_250 = y（ポーリングレート250Hz）

## タップ反応速度 (config/roBa.keymap)

- &mt の tapping-term-ms = 100ms（モディファイアタップの判定時間）
- &lt の tapping-term-ms = 150ms（レイヤータップの判定時間）

## トラックボール自動レイヤー (config/roBa.keymap)

- automouse-layer 無効化（コメントアウト）
- マウスレイヤーは &mo 4 のホールドで手動切り替え
