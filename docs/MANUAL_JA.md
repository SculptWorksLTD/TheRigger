# The Rigger — マニュアル

## 概要

The Rigger だけが無線機と通信し、各ソフトに専用の接続を用意します。WSJT-X、ログソフト、コンテストソフト、SDR ソフトが同じ無線機で同時に動きます。無線機を自動で見つけ、複数台を扱い、自動で更新します。自分から送信することはありません。

## インストール

**Windows**：`The-Rigger-Windows.zip` をダウンロードし、**The Rigger.exe** を自分のフォルダー（例：*ドキュメント*）に置いて開きます。「*Windows によって PC が保護されました*」と出たら **詳細情報 › 実行** を押します。OmniRig、com0com、Hamlib のインストールは不要です。デスクトップのショートカットは自動で作られます。

**Mac**：`The-Rigger-Mac.pkg`（Apple チップ）または `The-Rigger-Mac-Intel.pkg`（Intel）をダウンロードしてインストールします。開けない場合：*システム設定 › プライバシーとセキュリティ › このまま開く*。

## 初めての起動

無線機を USB ケーブルでつなぎ、電源を入れます。数秒で **無線機** タブに表示されます。The Rigger 側の設定は不要です。続けて下のとおり各ソフトを設定します。

## ソフトの接続

どの方式でも共通のルールは 3 つです。

- **PTT** は必ず **CAT**（または *無線機コマンドによる PTT*）。RTS や DTR は使いません。
- アドレスは必ず **127.0.0.1**（自分のコンピューター）。
- 設定後、ソフトで **Test**、**Connect** または **OK** を押します。

ソフトが対応している方式を選びます。

| 方式 | 設定する内容 | ソフト |
|---|---|---|
| Hamlib | *Hamlib NET rigctl* · `127.0.0.1:4532` | WSJT-X, JTDX, JS8Call, MacLoggerDX, Gpredict, CQRLOG, VarAC |
| flrig | *FLRig* · `127.0.0.1` ポート `12345` | fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog, Cloudlog) |
| TCI | *TCI* · `127.0.0.1:40001` | N1MM Logger+, MSHV, Log4OM, DXLog |
| OmniRig（Windows） | *OmniRig* · *Rig 1* | Log4OM, HDSDR, SDR Console, CW Skimmer, MMSSTV, UcxLog |
| Ham Radio Deluxe | サーバー `127.0.0.1` ポート `7809` | HRD Logbook, DM-780 |
| DXLab Commander | `127.0.0.1` ポート `52002` | BBLogger |
| ネットワーク CAT | 実機の機種または *Kenwood TS-2000* · `127.0.0.1:4600` | N1MM Logger+, DXLab Commander（機種 *Thetis*） |
| シリアルポート（Mac） | 実機の機種 · ポート `/tmp/TheRigger/…` · 速度は任意 | RUMlogNG, SkookumLogger |

### Hamlib（WSJT-X など）

1. **Rig**：*Hamlib NET rigctl*（ソフトによっては *rigctld*、モデル 2）。
2. **サーバー**：`127.0.0.1:4532`。
3. **PTT**：*CAT*。WSJT-X では **Test CAT** を押すと緑になります。

### flrig

1. **FLRig** を選びます（fldigi では *Rig Control › flrig › Connect to flrig*）。
2. アドレス `127.0.0.1`、ポート `12345`。flrig のインストールは不要です。

### TCI

1. **TCI** を選び、アドレス `127.0.0.1:40001`。
2. 音声はいつもどおり無線機のサウンドカードを使います。

### OmniRig（Windows のみ）

1. **OmniRig** を選び、**Rig 1**（2 台目は **Rig 2**）。本物の OmniRig はインストールしないでください。
2. ソフトは普通に起動します（*管理者として* 起動しない）。

### Ham Radio Deluxe

1. サーバー `127.0.0.1`、ポート `7809` で **Connect**。HRD Rig Control を開く必要はありません。
2. MMTTY と MMVARI：無料プラグイン **HRDPTT.mmr** をソフトのフォルダーにコピーし、ポートに **HRDPTT** を選びます。

### DXLab Commander（BBLogger）

1. BBLogger の *Preferences › CAT*：**IP** `127.0.0.1`、**ポート** `52002`、**Autostart** は空欄。CatBKT は不要です。
2. QSO ウィンドウで **CAT ON** を押します。

### ネットワーク CAT

1. 無線機として **実機の機種**（例：*IC-7100*）または **Kenwood TS-2000**、接続 **TCP**、`127.0.0.1` ポート `4600`。
2. DXLab Commander：**Model** *Thetis*、**Communicate via TCP**、`127.0.0.1` ポート `4600`。

### シリアルポート（Mac）

無線機として **実機の機種** または **Kenwood TS-2000**、ポート `/tmp/TheRigger/IC-7100-1`（名前は無線機によって変わります）、速度は任意、ハンドシェイクなし。1 つのソフトに 1 つのポートを使います。

### N3FJP（Windows）

*Rig Interface*：**None**。*Application Program Interface*：**TCP API Enabled** にチェック、ポート `1100`。バンド、モード、周波数が自動で入ります。

### 複数の無線機（10 台以上も可）

無線機ごとに専用のアドレスがあります。無線機 1 は無線機タブの 1 番目、無線機 2 は 2 番目、以下同様です。それ以降は表の間隔を足します。

| 方式 | 無線機 1 | 無線機 2 | 無線機 3 | 1 台増えるごと | 無線機 10 |
|---|---|---|---|---|---|
| Hamlib | 4532 | 4534 | 4536 | +2 | 4550 |
| flrig | 12345 | 12346 | 12347 | +1 | 12354 |
| TCI | 40001 | 40002 | 40003 | +1 | 40010 |
| DXLab Commander | 52002 | 52102 | 52202 | +100 | 52902 |
| ネットワーク CAT | 4600 | 4601 | 4602 | +1 | 4609 |
| Ham Radio Deluxe | 無線機 1 | 無線機 2 | 無線機 3 | 同じポート 7809 | 無線機 10 |
| OmniRig | Rig 1 | Rig 2 | — | 2 台まで（OmniRig の制限） | — |

同じ機種が 2 台あると、たとえば *IC-7300* と *IC-7300 2* になります。3 台以上の場合、OmniRig 対応ソフトに見えるのは最初の 2 台だけです。ほかは Hamlib、flrig、TCI を使ってください。

### 一覧にないソフト

ソフトの設定で次の項目をこの順に探します：*Hamlib/rigctld*、*FLRig*、*TCI*、*OmniRig*、*Ham Radio Deluxe*、*TCP*。見つかった方式の行を使います。COM ポートしか使えない Windows ソフト（Logger32、Win-Test、SatPC32）は接続できません。Log4OM、N1MM、Gpredict を使ってください。

## ウィンドウ

- **無線機**：見つかった無線機の周波数、モード、接続中のソフト。カードの電源ボタンで無線機をほかのソフト（メーカー純正ソフトなど）に明け渡します。無線機本体の電源は切れません。
- **マニュアル**：このマニュアル。
- **設定**：言語、自動起動、*非表示で起動*、更新、ポートとドライバー。

The Rigger は起動のたびに自動で更新されます。

## Windows のみ

- **競合するソフト**：本物の OmniRig、CatBKT、DXLab Commander、flrig、rigctld、HRD、仮想 COM ポートのソフトが無線機やポートをふさぐと、無線機タブに黄色い行が出ます。**見る** で一覧が開き、**閉じる…**、**アンインストール…**、**クリーンアップ…**（レジストリに残った OmniRig）が使えます。
- **com0com のクリーンアップ**：*設定 › ポートとドライバー › クリーンアップ…* で com0com と仮想ポートを削除します。注意書きを読んで確認し、最後に再起動します。
- **USB ドライバー**：足りない場合、The Rigger が公式ドライバーを自動でインストールします。

## 報告とアイデア

右上の吹き出しボタン：**うまく動かない** または **アイデア・要望**。前回の起動のログを添付してください。匿名で、コールサインは任意です。*送信内容をそのまま見る* で送信前にすべて確認できます。

## よくある問題

- **無線機が表示されない**：電源とケーブルを確認し、*無線機を再検索* を押します。無線機の USB ポートを直接開くソフトは閉じてください。
- **ソフトが接続しない**：表で方式とアドレスをもう一度確認します。The Rigger より先にソフトを開いていた場合は、もう一度 *Test* または *Connect* を押します。
- **PTT が動かない**：ソフトの PTT を **CAT** にします。
- **OmniRig が見つからない**：The Rigger を一度開いてから、ソフトを開き直します（管理者としては開かない）。

---

The Rigger · IU1MVI 製ソフトウェア · すべてのアマチュア無線家に無料。OmniRig 互換は VE3NEA による OmniRig の公開インターフェース（MIT ライセンス）を使っています。Hamlib、flrig、TCI、Ham Radio Deluxe は各権利者の商標です。73!
