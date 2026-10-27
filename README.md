# gndless_iec60958

S/PDIFとAES3のRTL実装です。

依存はVeryl stdのみ。sampleはIEC60958のpayload型、preamble・parity・192-frame block scheduler・channel status・AES3 CRCを共通契約で扱います。BMC serializer、subframe、stereo I/O、status streamは内部APIです。物理linkの同期化責任は利用者にあります。

S/PDIF consumerのchannel statusはIEC 60958-3 Mode 0に従い、Byte 0のnon-audio/Cp/emphasisとByte 4のoriginal sampling frequencyを生成します。S/PDIFに768kHzのoriginal codeはないため、768kHzではoriginal sampling frequencyをnot indicatedにします。AES3はCRC-8を付加します。

```veryl
inst tx: iec60958::SpdifTransmitter (...);
inst rx: iec60958::Aes3Receiver (...);
```
