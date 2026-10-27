# Changelog

## [0.2.0] - 2026-10-27

### Fixed

- S/PDIF consumer channel statusのByte 0をIEC 60958-3 Mode 0のbit配置へ修正した。non-audioをbit 1、Cpをbit 2、emphasisをbits 3-5へ移した
- S/PDIF consumer channel statusのByte 4を修正し、original sampling frequencyをbits 4-7へone's complement codeで出力するようにした
- `test_iec60958_channel_status_bit`をクロック同期のgolden vector testへ置き換え、S/PDIF/AES3のByte 0-4を検証するようにした

### BREAKING CHANGE

- `SpdifTransmitter`の`emphasis` portを2bitから3bitへ変更した

### Changed

- `SpdifChannelStatusBit`と`SpdifTransmitter`の`emphasis` portを3bitへ変更した
- 公開transceiverのport doc commentを追加し、説明文を日本語と単一行段落へ整理
- doc commentの句点と体言止めの表記を整理
- doc commentのsummary表記を統一
- 各testのdoc commentを検証目的が分かる表現へ統一

- IEC60958共通型packageをproject名と重複する`Iec60958`から`Types`へ改名
- 公開transceiverへstereo sample handshake、A/B subframe、RX backpressureのWavedromを追加

- IEC60958共通codec、S/PDIF、AES3を独立packageへ移動
