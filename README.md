# こえきゃぷ (KoeCap) for OBS

声で話した「いまやっていること」を字幕として出すOBS拡張機能です。

## できること

- 字幕の操作が声でできます。
- キーワードでOBSの操作もできます。

## ダウンロード（最新の版 0.3.0）

- [**はじめての方**　こえきゃぷをダウンロード](https://github.com/kurus-es/koecap/releases/latest/download/KoeCap.zip)
- [**使っている方**　最新の版に更新（0.3.0 以降）](https://github.com/kurus-es/koecap/releases/latest/download/KoeCap-update.zip)

## インストール

1. **zip を展開する**  
   `KoeCap` フォルダを好きな場所に置きます（例: `ドキュメント\KoeCap`）
2. **OBS にスクリプトを足す**  
   OBS の「ツール」→「スクリプト」→「＋」→ `KoeCap` フォルダの `koecap.lua` を選びます
3. **OBS にドックを足す**  
   OBS の「ドック」→「カスタムブラウザドック」で  
   ドック名： `こえきゃぷ`  
   URL： `http://localhost:8765/`  
   と書いて「適用」を押します。

くわしい使い方は zip の中の `README.txt` にあります

## 動作環境

- Windows 10 / 11（64bit）
- OBS Studio 30 以降
- メモリ 最小 8GB以上、推奨 16GB以上
- ディスク 空き容量 1GB以上推奨

## インターネットとの通信

音声モデルを取りに行くときだけ、インターネットにつなぎます（`model` フォルダ・`reazonspeech` フォルダが無いとき）。

- キーワード検出用 Vosk small-ja 0.22（約 50 MB）… alphacephei.com
- 高精度認識用 ReazonSpeech（約 680 MB・保存は約 155 MB）… github.com/k2-fsa/sherpa-onnx

利用状況・新しい版の確認は送っていません。ドックとアプリのやり取りは、このパソコンの中だけ（`localhost`）です。

## ライセンス

### こえきゃぷ本体

こえきゃぷは **GNU General Public License version 3（GPL-3.0）** で配布します（[LICENSE.txt](LICENSE.txt)）。
同梱の pykakasi が GPL-3.0 のためです。ソースコードは、各版のソースの zip（例: `KoeCap-0.3.0-source.zip`）です。

こえきゃぷは無保証です。使ったこと・使えなかったことで起きたことについて、作成者は責任を負いません（GPL-3.0 の「保証の否認」「責任の制限」のとおり）。

### zip に入っている部品

ライセンス文は zip の `python\licenses\<名前>\` に、Python 本体とその中の部品のものは `python\LICENSE.txt` にあります。
zlib・Expat・libmpdec・HACL\* の 4 つは、`python\LICENSE.txt` に文が無いため、文の全体を zip の `licenses\python-extra\` に入れています。

**Python 本体（`python\`）**

| もの | ライセンス |
|---|---|
| Python 3.12.10（Python 公式の Windows 用の埋め込み版） | PSF License（Python Software Foundation License Version 2） |
| Microsoft Visual C++ のランタイム（vcruntime140.dll・vcruntime140_1.dll） | Microsoft の再頒布可能コード（条件は `python\LICENSE.txt`） |
| OpenSSL 3.0.16（Python の中） | Apache-2.0（文は `python\LICENSE.txt` にある） |
| bzip2 1.0.8（Python の中） | bzip2 License（BSD 系） |
| libffi（Python の中） | MIT |
| zlib 1.3.1（Python の中） | zlib License（文の全体は `licenses\python-extra\zlib.txt`） |
| Expat 2.7.1（Python の中） | MIT 系（文の全体は `licenses\python-extra\expat.txt`） |
| libmpdec 2.5.1（Python の中） | BSD 系 2 か条（文の全体は `licenses\python-extra\libmpdec.txt`） |
| SQLite 3.49.1（Python の中） | パブリックドメイン |
| liblzma（xz 5.2.5・Python の中） | パブリックドメイン |
| HACL\*（Python の中） | MIT（INRIA, CMU and Microsoft Corporation／HACL\* Contributors。文の全体は `licenses\python-extra\hacl-star.txt`） |

**ライブラリ（`python\lib\`）**

| もの | 版 | ライセンス |
|---|---|---|
| pykakasi | 2.3.0 | GPL-3.0 |
| vosk | 0.3.45 | Apache-2.0 |
| Kaldi（vosk の libvosk.dll の中） | — | Apache-2.0 |
| libgcc・libstdc++（vosk の中の libgcc_s_seh-1.dll・libstdc++-6.dll） | GCC 10 | GPL 3 ＋ GCC Runtime Library Exception 3.1 |
| libwinpthread（vosk の中の libwinpthread-1.dll） | mingw-w64 8.0.0 | MIT 系 ＋ BSD 系 3 か条（Lockless Inc.） |
| sherpa-onnx・sherpa-onnx-core | 2.0.1 | Apache-2.0 |
| ONNX Runtime（sherpa-onnx の中の onnxruntime.dll） | — | MIT |
| sounddevice | 0.5.6 | MIT |
| PortAudio（sounddevice の中・64bit 用の libportaudio64bit.dll だけ） | — | MIT 系（PortAudio License） |
| requests | 2.34.2 | Apache-2.0（NOTICE あり） |
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

**GCC の部品の元のソース**
libgcc・libstdc++・libwinpthread は、vosk に入っている形のまま（作り直さずに）配っています。
GCC 10（gcc-10 の枝の 2021-01-10 の写し）・mingw-w64 8.0.0。Debian 系の mingw-w64 クロスコンパイラ（gcc-mingw-w64 24.2）で作られたものです。
元のソースは https://gcc.gnu.org/ と https://www.mingw-w64.org/ で手に入ります。

## 使用する際にダウンロードされるもの

次のものは zip に入っていません。こえきゃぷがはじめて使うときに、使う人のパソコンへ配布元から直接ダウンロードします（こえきゃぷは配り直していません）。ライセンスは配布元の表示によります。

| もの | いつ | 配布元 | ライセンス |
|---|---|---|---|
| Vosk の日本語モデル small-ja 0.22（vosk-model-small-ja-0.22・約 50 MB） | `model` フォルダが無いとき | alphacephei.com | Apache-2.0（配布元の表示・Alpha Cephei） |
| ReazonSpeech の k2 モデル（sherpa-onnx-zipformer-ja-reazonspeech-2024-08-01・約 680 MB） | 認識の方式が「高精度」で、`reazonspeech` フォルダが足りないとき | github.com/k2-fsa/sherpa-onnx | Apache-2.0（配布元の表示。reazon-research/reazonspeech-k2-v2 を sherpa-onnx の形に変えたもの） |
