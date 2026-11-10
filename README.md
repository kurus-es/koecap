# こえきゃぷ (KoeCap) for OBS

声で話した「いまやっていること」を、OBS の画面に字幕として出すアプリです。

- キーワード（例:「いまやっていることは」）のあとに話した 1 文が、字幕になります。
- キーワードで、字幕を消す・ひとつ前に戻す・OBS のホットキーを押す などの操作もできます（声のコマンド）。
- 声の聞き取りは、このパソコンの中だけでします。声・字幕・設定をインターネットに送ることはありません。

最新の版: **0.3.0**（[ダウンロード](../../releases/latest)）

---

## ダウンロード

[Releases](../../releases) から、使うものを 1 つ選びます。

| ファイル | どんなとき |
|---|---|
| `KoeCap-0.3.0.zip`（約 39 MB） | **はじめて入れる**とき |
| `KoeCap-update-0.20-to-0.3.0.zip` | 0.20 以降の版から**更新する**とき |
| `KoeCap-0.3.0-source.zip` | ソースコード（GPL-3.0） |

## 動かすのに必要なもの

- Windows 10 / 11（64bit）
- OBS Studio 30 以降
- インターネット（はじめに音声モデル 約 730 MB をダウンロードするときだけ）
- ディスク 約 400 MB・パソコンのメモリ 8 GB 以上（ゲームを配信するときは 16 GB 以上をおすすめ。こえきゃぷは約 2 GB を使います）

Python などを別に入れる必要はありません（アプリ専用の Python が zip に入っています）。

## 入れ方

1. **zip を展開する**
   できた `KoeCap` フォルダを好きな場所に置きます（例: `ドキュメント\KoeCap`）。
2. **OBS にスクリプトを足す**
   OBS の「ツール」→「スクリプト」→「＋」→ `KoeCap` フォルダの `koecap.lua` を選びます。
   はじめての時は、音声モデルのダウンロードを始めます（数分。待つだけで大丈夫です）。
   このとき「アプリを再起動」は押さなくてかまいません（押すとダウンロードがやり直しになります）。
3. **OBS にドックを足す**
   OBS の「ドック」→「カスタムブラウザドック」で、次の 2 つを書いて「適用」を押します。
   - ドック名: `こえきゃぷ`
   - URL: `http://localhost:8765/`
4. **字幕のソースを足す**
   ドックの右下の「⚙」→「出力先」→ 出力先 1 の「テキスト(GDI+)を追加」を押します。
5. **話してみる**
   左上の「← 戻る」でふだんの画面に戻り、ドックのいちばん上が「聞き取り中」になったら、「いまやっていることは、〇〇」と話します。画面に「〇〇」が出れば完了です。

くわしい使い方は、zip の中の `README.txt` を見てください。

## 更新のしかた

1. OBS を閉じる（こえきゃぷも自動で終わります）
2. 更新用の zip を展開し、中の `KoeCap` フォルダの**中身**を、今の `KoeCap` フォルダに上書きでコピーする
   （「ファイルの置き換え」を聞かれたら「ファイルを置き換える」）
3. OBS を起動する

上書きしても、設定は消えません。版ごとに変わったことは、更新用の zip の `UPDATE.txt` にあります。

## 困ったとき

- **ドックに「接続できません」と出る** … OBS の「ツール」→「スクリプト」→ `koecap.lua` を選び、「アプリを再起動」を押す。ほかのアプリがポート 8765 を使っていないかも見る。
- **更新したのにドックが古い画面のまま** … 「アプリを再起動」を押し、ドックの上で右クリック →「再読み込み」。
- **音声モデルのダウンロードに失敗する** … `README.txt` の「7. 困ったとき」の手順で、手で入れられます。
- **それでも直らない** … ドックの「⚙」→「設定」→「その他」→「報告用にまとめる」で zip を作り、このリポジトリの [Issues](../../issues) に、起きたことと一緒に添えてください。
  ※ Issues は誰でも読めます。報告用の zip には、聞こえた言葉やキーワードの言葉（ログと設定）が入るので、人に見せてよいか確かめてから添えてください。

作成者は、使い方の相談や不具合の修正を約束するものではありません。

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
