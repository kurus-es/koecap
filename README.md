# こえきゃぷ (KoeCap) for OBS

声で話した「いまやっていること」を字幕として出すOBS拡張機能です。

## できること

- 字幕の操作が声でできます。
- キーワードでOBSの操作もできます。

## ダウンロード

- [**はじめての方**　こえきゃぷをダウンロード](https://github.com/kurus-es/koecap/releases/latest/download/KoeCap.zip)
- [**使っている方**　最新の版に更新](https://github.com/kurus-es/koecap/releases/latest/download/KoeCap-update.zip)

## インストール

1. **zip を展開する**  
   `KoeCap` フォルダを好きな場所に置きます。
2. **OBS にスクリプトを足す**  
   OBS の「ツール」→「スクリプト」→「＋」→ `KoeCap` フォルダの `koecap.lua` を選びます。
3. **OBS にドックを足す**  
   OBS の「ドック」→「カスタムブラウザドック」で  
   ドック名： `こえきゃぷ`  
   URL： `http://localhost:8765/`  
   と書いて「適用」を押します。

くわしい使い方は zip の中の `README.txt` にあります。

## 動作環境

- Windows 10 / 11 64bit
- OBS Studio 30 以降
- メモリ 8GB以上、推奨 16GB以上
- ディスク 空き容量 1GB以上推奨

## インターネットとの通信

音声モデルを取りに行くときだけ、インターネットにつなぎます。

- キーワード検出用 Vosk small-ja 0.22… alphacephei.com
- 高精度認識用 ReazonSpeech… github.com/k2-fsa/sherpa-onnx

利用状況・新しい版の確認は送っていません。ドックとアプリのやり取りは、このパソコンの中だけです。

## ライセンス

### こえきゃぷ本体

こえきゃぷは **GNU General Public License version 3** で配布します。
同梱の pykakasi が同じライセンスのためです。ソースコードは、各版のソースの zip です。

こえきゃぷは無保証です。使ったこと・使えなかったことで起きたことについて、作成者は責任を負いません。

### ソフトウェア・ライブラリ他

**Python 本体**

| ソフトウェア | ライセンス |
|---|---|
| Python 3.12.10 | PSF License |
| Microsoft Visual C++ のランタイム | Microsoft の再頒布可能コード |
| OpenSSL 3.0.16 | Apache-2.0 |
| bzip2 1.0.8 | bzip2 License |
| libffi | MIT |
| zlib 1.3.1 | zlib License |
| Expat 2.7.1 | MIT 系 |
| libmpdec 2.5.1 | BSD 系 2 か条 |
| SQLite 3.49.1 | パブリックドメイン |
| liblzma | パブリックドメイン |
| HACL\* | MIT |

**ライブラリ**

| ライブラリ | 版 | ライセンス |
|---|---|---|
| pykakasi | 2.3.0 | GPL-3.0 |
| vosk | 0.3.45 | Apache-2.0 |
| Kaldi | ※vosk 同梱 | Apache-2.0 |
| libgcc・libstdc++ | ※vosk 同梱 | GPL 3 ＋ GCC Runtime Library Exception 3.1 |
| libwinpthread | ※vosk 同梱 | MIT 系 ＋ BSD 系 3 か条 |
| sherpa-onnx・sherpa-onnx-core | 2.0.1 | Apache-2.0 |
| ONNX Runtime | ※sherpa-onnx 同梱 | MIT |
| sounddevice | 0.5.6 | MIT |
| PortAudio | ※sounddevice 同梱 | MIT 系 |
| requests | 2.34.2 | Apache-2.0 |
| certifi | 2026.10.23 | MPL-2.0 |
| tqdm | 4.70.1 | MIT と MPL-2.0 |
| urllib3 | 2.8.0 | MIT |
| charset-normalizer | 3.5.2 | MIT |
| srt | 3.5.3 | MIT |
| jaconv | 0.5.0 | MIT |
| deprecated | 3.0.0 | MIT |
| cffi | 2.1.1 | MIT No Attribution |
| colorama | 0.4.6 | BSD-3-Clause |
| idna | 3.20 | BSD-3-Clause |
| websockets | 17.3 | BSD-3-Clause |
| pycparser | 3.12 | BSD-3-Clause |
| wrapt | 2.5.1 | BSD-2-Clause |

libgcc・libstdc++・libwinpthread の元のソースは https://gcc.gnu.org/ と https://www.mingw-w64.org/ で手に入ります。

## 使用する際にダウンロードされるファイル

次のファイルは zip に入っていません。はじめて使うときに、こえきゃぷが使う人のパソコンへ配布元から直接ダウンロードします。ライセンスは配布元の表示によります。

| モデル | 配布元 | ライセンス |
|---|---|---|
| Vosk の日本語モデル small-ja 0.22 | alphacephei.com | Apache-2.0 |
| ReazonSpeech の k2 モデル | github.com/k2-fsa/sherpa-onnx | Apache-2.0 |

## 最新の版と問い合わせ

最新の版: 0.3.0

困ったときは [Issues](../../issues) へ。報告用の zip には聞こえた言葉やキーワードの言葉が入るので、人に見せてよいか確かめてから添えてください。
