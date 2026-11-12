# The Rigger — マニュアル

## できること

The Rigger は、無線機とコンピューター上のソフトをつなぐ交換台です。

ふつう無線機の CAT ポートは一度に 1 つのソフトしか使えません。WSJT-X が開くと、ログソフトはもう見つけられません。The Rigger なら違います。無線機と話すのは The Rigger だけで、各ソフトにそれぞれ専用の接続を渡します。だから WSJT-X、ログソフト、コンテストソフト、CWIU1MVI、SDR ソフトなどが、同じ無線機で邪魔し合わずに同時に動きます。

まとめると：

- **無線機を自動で見つけます**：USB ケーブルをつなぐだけで無線機が現れます。ポートも速度も機種も選ぶ必要はありません。
- **複数の無線機を同時に**：それぞれに専用の接続があります。
- **ソフトが使うあらゆる接続**：Hamlib、flrig、TCI、OmniRig（Windows）、Ham Radio Deluxe、ネットワーク CAT、シリアルポート（Mac と Linux）。
- **自動でアップデート**し、7 か国語に対応します。

The Rigger が勝手に送信したり、無線機の設定を変えたりすることはありません。ソフトが求めたことだけを行います。

## インストール

GitHub のプロジェクト（SculptWorksLTD/TheRigger）の **Releases** ページから、お使いのシステム用のファイルをダウンロードします。

### Windows

1. `The-Rigger-…-Windows.zip` をダウンロードします。
2. zip を開き、**The Rigger.exe** を自分のフォルダー（例：*ドキュメント › The Rigger*）にドラッグします。zip の中や一時的なダウンロードフォルダーに置いたままにしないでください。
3. **The Rigger.exe** をダブルクリックします。
4. 「*Windows によって PC が保護されました*」と出たら、**詳細情報** → **実行** を押します。これは最初の 1 回だけです。

ほかに入れるものはありません。OmniRig も com0com も Hamlib も不要です。

### macOS

1. Apple チップ（M1、M2、M3、M4）の Mac なら `The-Rigger-…-Mac.pkg`、Intel の Mac なら `The-Rigger-…-Mac-Intel.pkg` をダウンロードします。
2. ファイルを開いてインストールを進めます。The Rigger は **アプリケーション** に入ります。
3. Mac が開けないと言う場合：ファイルを右クリック › **開く**、または *システム設定 › プライバシーとセキュリティ › このまま開く*。

以後、The Rigger は自動でアップデートされます。

## 初めての起動

起動するとクレジット入りのようこそ画面が出ます。**はじめる · 73** を押してください。

無線機を USB ケーブルでつなぎ、電源を入れます。数秒で The Rigger が見つけます。USB ポート、プロトコル（Icom CI-V、Kenwood、Elecraft、Yaesu、FT-817）、速度を試し、機種を判別します。設定は何もいりません。

**無線機** タブに無線機が出たら準備完了です。各ソフトの設定方法は、このマニュアルの **ソフト別の手順** の章を見てください。

## ウィンドウ

ウィンドウには上部中央で切り替える 3 つのタブがあります：

- **無線機**：見つかった無線機。周波数、モード、接続中のソフトを表示します。
- **マニュアル**：このマニュアル。左側に目次があります。
- **設定**：言語、起動、アップデート、ポート、情報。

右上には 2 つのボタンがあります：

- **しまう**（下向き矢印）：ウィンドウを隠します。Mac ではメニューバーの時計の近くに残るので、アイコンをクリックして *The Rigger を表示* を選びます。Windows ではタスクバーに入ります。
- **電源**（⏻）：The Rigger を終了します。もう一度開くまで、接続中のソフトは無線機を使えません。

下部はステータスバーです。無線機が 1 台以上つながっていればランプは緑、注意があれば黄色です。円形矢印のボタンで無線機を再検索します。右端はバージョンです。

ウィンドウの端をドラッグすると大きさを変えられます。

## 無線機タブ

見つかった無線機ごとにカードがあります。

### 見出し

- **電源ボタン**（左）：*The Rigger の中で* 無線機をオン・オフします。オフにすると The Rigger は USB ポートを閉じて空けます。メーカーのソフトやファームウェア更新に使うときに便利です。もう一度押すと戻ります。無線機本体の電源は切れません。
- **名前**：機種名。同じ機種が 2 台あれば番号が付きます（例：*IC-7300 2*）。
- **状態**：*接続中*（応答あり）、*未接続*（ケーブルが外れている、または電源オフ）、*オフ*（The Rigger でオフ）。

### 表示部

- 使用中 VFO の **周波数** を大きく表示し、横に **モード**（USB、LSB、CW、CW-R、RTTY、AM、FM、USB-D、LSB-D、FM-D）。
- **A** と **B**：使用中の VFO。
- **SPLIT**：スプリット中に点灯。
- **TX**：送信中は赤になります。
- その下：もう一方の VFO の周波数と **S メーター** のバー。

ダイヤルを回したときも、ソフトが周波数を変えたときも、表示はリアルタイムで追従します。

### 無線機の情報

灰色の行には機種、USB ポート、速度、そして The Rigger でオンなら番号（**Rig 1**、**Rig 2**…）が出ます。この番号は OmniRig と Ham Radio Deluxe で使います。

### 接続中のソフト

この無線機を使っているソフトの一覧です。それぞれにランプがあります：

- **緑**：無線機と通信中。
- **黄色**：接続しているが、いまは何も問い合わせていない。

右側は使っている接続（例：`tcp:4532`、`flrig`、`TCI`、シリアルポート）です。クリックするとアドレスをコピーします。

### ボタン

- **接続テスト**：ソフトのふりをして、各接続（シリアルポート、Hamlib、flrig、ネットワーク CAT、TCI）から周波数を読みます。**✓** の行は正常、**✗** の行は問題ありです。テストは読むだけで、送信も変更もしません。

### 無線機を再検索

**無線機を再検索** ボタン（タブの右上、または下部の円形矢印）で、すぐにすべての USB ポートを確認し直します。見えていなかった無線機の電源を入れたあとや、ポートをふさいでいたソフトを閉じたあとに使います。

## 接続方法

The Rigger は無線機ごとに、これらの接続をすべて同時に開きます。各ソフトは知っている接続を使い、同じ接続を複数のソフトで共有できます。

| 接続 | アドレス（1 台目） | 2 台目 | システム |
|---|---|---|---|
| Hamlib NET rigctl | 127.0.0.1:4532 | 127.0.0.1:4534 | すべて |
| flrig | 127.0.0.1:12345 | 127.0.0.1:12346 | すべて |
| TCI | 127.0.0.1:40001 | 127.0.0.1:40002 | すべて |
| ネットワーク CAT（Kenwood TS-2000） | 127.0.0.1:4600 | 127.0.0.1:4601 | すべて |
| Ham Radio Deluxe | 127.0.0.1:7809（無線機 1） | 同じポート、無線機 2 | すべて |
| OmniRig | Rig 1 | Rig 2 | Windows |
| シリアルポート | /tmp/TheRigger/… | /tmp/TheRigger/… | Mac と Linux |

ポートがほかのソフト（本物の flrig や rigctld など）に使われているときは、The Rigger は次の空きポートを使います。正確なアドレスは、無線機カードの *接続テスト* で確認できます。

### Hamlib NET rigctl

WSJT-X、JTDX、JS8Call、FreeDV、Gpredict、CQRLOG、KLog、MacLoggerDX、Pat など、Hamlib を使うすべてのソフトの接続です。

ソフトで無線機に **Hamlib NET rigctl**（ソフトによっては *NET rigctl* や *rigctld*、Hamlib のモデル番号 2）を選び、サーバーに表示されたアドレス（例：`127.0.0.1:4532`）を入れます。PTT は **CAT** にします。

### flrig

The Rigger は flrig（W1HKJ）とまったく同じように応答します。fldigi、QLog、Not1MM、HAMRS、WaveLogGate（Wavelog と Cloudlog）、WFDlogger など、*FLRig* の選択肢があるすべてのソフトの接続です。

ソフトで **FLRig** を選び、アドレス `127.0.0.1`、ポート `12345`（2 台目は `12346`）にします。flrig のインストールは不要です。

### TCI

The Rigger は TCI 機器（Expert Electronics のプロトコル）として応答します。N1MM Logger+、JTDX、MSHV、Log4OM、QLog、Swisslog、DXLog などが使います。

ソフトで **TCI** を選び、アドレス `127.0.0.1:40001`（2 台目は `40002`）にします。The Rigger の TCI は周波数、モード、PTT、スプリットを扱います。音声はいつもどおり無線機のサウンドカードを使います。

### OmniRig（Windows のみ）

The Rigger が OmniRig の代わりになります。**OmniRig のインストールは不要です**。ソフトで **OmniRig** を選び、The Rigger でオンの 1 台目なら **Rig 1**、2 台目なら **Rig 2** を選びます。

Log4OM、DXLog.net、HDSDR、SDR Console、CW Skimmer、UcxLog、Swisslog、MixW、QARTest、VarAC など、OmniRig を使うすべてのソフトで、32 ビットでも 64 ビットでも動きます。The Rigger が閉じているときにソフトが OmniRig を求めると、Windows が The Rigger を隠れた状態で自動起動します。

本物の OmniRig も入っている場合でも、ソフトは The Rigger を見つけます。ただし *管理者として* 起動したソフトは除きます。ふつうに起動してください。同じ無線機で両方を同時に動かさないでください。

### Ham Radio Deluxe

The Rigger は *HRD Rig Control* として応答します。HRD Logbook、DM-780、そして Ham Radio Deluxe につなぐソフト（*Ham Radio Deluxe* を選んだ WSJT-X や JTDX も）に使えます。

ソフトでサーバー `127.0.0.1`、ポート `7809` を設定します。無線機の名前は The Rigger と同じで、「無線機」タブの順に 1、2、3… と番号が付きます。

### ネットワーク CAT（TCP）

無線機のシリアルポートのようにふるまうアドレスです。N1MM Logger+ や MSHV など、TCP で無線機につなげるソフトに向いています。

ソフトで無線機に **実際の機種**（例：*IC-7100*）か **Kenwood TS-2000** を選び、ポートに表示されたアドレス（例：`127.0.0.1:4600`）を入れます。PTT は **CAT** です。

### シリアルポート（Mac と Linux）

シリアルポートしか使えないソフトのために、The Rigger は無線機ごとに仮想ポートを作ります。例：`/tmp/TheRigger/IC-7100-1`、`/tmp/TheRigger/IC-7100-2`…

ソフトで **実際の機種** か **Kenwood TS-2000**、表示されたポート、速度は **何でも可**、ハンドシェイクは **なし**、PTT は **CAT** を選びます。

各ポートはソフトの言語を自動で判別します：Icom CI-V、Kenwood、Elecraft、Yaesu、FT-817、TS-2000。実際の機種を選ぶと、特殊なものも含めすべてのコマンドが無線機に届きます。TS-2000 では周波数、モード、PTT、スプリットが使えます。

1 つのポートに 1 つのソフト：The Rigger は各ソフトに別のポートを割り当てます。無線機ごとのポート数は設定で変えられます（1〜16）。

Windows では The Rigger は仮想 COM ポートを作りません。ドライバーのいらないほかの接続を使ってください。

### CWIU1MVI

CWIU1MVI は The Rigger を自動で見つけます。CWIU1MVI の無線機一覧で **The Rigger · 無線機名** を選ぶだけです。ほかの設定はいりません。

## ソフト別の手順

よく使われるソフトの手順です。アドレスは 1 台目の無線機のものです。ほかの無線機は *接続方法* の章の表を見てください。

### WSJT-X、JTDX、JS8Call、WSJT-Z

1. *File › Settings › Radio*。
2. **Rig**：*Hamlib NET rigctl*。
3. **Network Server**：`127.0.0.1:4532`。
4. **PTT Method**：*CAT*。
5. **Mode**：無線機を USB-D にしたいなら *Data/Pkt*、そうでなければ *USB*。
6. **Split Operation**：お好みで *Rig* か *Fake It*。
7. **Test CAT** を押すと緑になります。最後に **OK**。

### fldigi

1. *Configure › Config dialog › Rig Control › flrig*。
2. **Connect to flrig** にチェック、アドレス `127.0.0.1`、ポート `12345`。
3. *Hamlib* と *RigCAT* にチェックがあれば外します。
4. **Save** して閉じます。fldigi の周波数が無線機に追従します。

### Log4OM 2（Windows）

1. *Settings › CAT interface*。
2. **CAT engine**：*OmniRig*。**Rig**：*Rig 1*（2 台目は *Rig 2*）。
3. **Autostart** にチェックして **Connect** を押します。

OmniRig のインストールは不要です。代わりに *Hamlib* › *Connect to active HAMLIB interface*、ポート `4532` も使えます。

### N1MM Logger+（Windows）

1. *Config › Configure Ports, Mode Control, Winkey, etc… › Hardware*。
2. ポートの行で **TCP**、**Radio**：*IC-7100*（実際の機種）または *Kenwood TS-2000* を選びます。
3. **Set** を押し、アドレス `127.0.0.1`、ポート `4600` を入力します。
4. **PTT via Radio Command** をオンにします。
5. **OK**：左下に周波数が出ます。

N1MM は **TCI**（`127.0.0.1:40001`）も使えます。

### HRD Logbook と DM-780（Windows）

無線機への接続画面でサーバー `127.0.0.1`、ポート `7809` を選び、**Connect** を押します。*HRD Rig Control* を開く必要はありません。The Rigger が応答します。

### QLog

1. *Settings › Equipment › Rig* で無線機を追加します。
2. **Interface**：*FLRig*、ホスト `127.0.0.1`、ポート `12345`（または *Hamlib* › *NET rigctl* で `127.0.0.1:4532`）。
3. 保存し、*Equipment* メニューから無線機に接続します。

### MacLoggerDX（Mac）

1. *Prefs › Radio*。
2. **Hamlib rigctld** を選び、ホスト `127.0.0.1`、ポート `4532`。
3. コントロール画面で **Radio VFO** をオンにします。

代わりに実際の機種と `/tmp/TheRigger/` のポートを選ぶこともできます。

### RUMlogNG と SkookumLogger（Mac）

無線機の環境設定で **実際の機種**（または Kenwood TS-2000）と `/tmp/TheRigger/` のポート（例：`/tmp/TheRigger/IC-7100-2`）を選びます。速度は何でもかまいません。

### Wavelog と Cloudlog（WaveLogGate 経由）

WaveLogGate で *Config › Radio* を開き、**FLRig**、ホスト `127.0.0.1`、ポート `12345` を選んで保存します。Wavelog が周波数とモードを受け取り、変更もできます。

### HAMRS、Not1MM、WFDlogger

無線機制御の設定で **FLRig**、ホスト `127.0.0.1`、ポート `12345` を選びます。

### MSHV

*Options › Radio and Network Configuration*：**TCI** とアドレス `127.0.0.1:40001` を選びます。

### HDSDR、SDR Console、CW Skimmer（Windows）

**OmniRig** を選び（HDSDR は *Options › CAT to Radio (Omni-Rig)*、SDR Console は *Radio › External Radio*、CW Skimmer は *Setup › Radio*）、**Rig 1** にします。

### Gpredict

*Edit › Preferences › Interfaces › Radios › Add new*：ホスト `localhost`、ポート `4532`、種類は *RX + TX* など必要なもの。

### CQRLOG（Linux）

*Preferences › TRX control*：*Run rigctld* のチェックを外し、**Rig model**：*2 Hamlib NET rigctl*、**Device**：`127.0.0.1:4532`。

### VarAC（Windows）

*Settings › Rig control*：**OmniRig** と *Rig 1*、または **Hamlib (rigctld)** で `127.0.0.1`、ポート `4532`。

### DXLab Commander（Windows）

Commander は OmniRig も Hamlib も使えませんが、ネットワークで Thetis と話せます。The Rigger は Thetis として応答します。

1. *Config › Ports* の無線機の欄で **Model**：*Thetis*。
2. **Communicate via TCP** にチェック、**IP Address** `127.0.0.1`、**IP Port** `4600`（2 台目は `4601`）。
3. 設定を閉じると Commander に周波数が出ます。DXKeeper、SpotCollector など DXLab スイート全体も使えます。

### N3FJP ACLog と N3FJP のコンテストソフト（Windows）

N3FJP のソフトは COM ポートなしでは無線機を共有できませんが、ネットワークインターフェースがあります。The Rigger がそれを使って、オンになっている 1 台目の無線機のバンド、モード、周波数を自動で送ります。

1. *Settings › Rig Interface*：**None** を選びます。
2. *Settings › Application Program Interface*：**TCP API Enabled (Server)** にチェック、ポート `1100`。
3. 完了です。バンド、モード、周波数が自動で入ります。The Rigger が勝手に QSO を記録することはありません。

この方法では、ACLog から無線機の周波数を変えることはできません（スポットのクリックなど）。

### MMSSTV、MMTTY、MMVARI（Windows）

- **MMSSTV**：*Option › Setup › TX › Radio command* で **OmniRig** と *Rig 1* を選びます。
- **MMTTY と MMVARI**：無料プラグイン **HRDPTT.mmr**（MM ソフトを Ham Radio Deluxe とつなぐもの）をダウンロードしてソフトのフォルダーにコピーし、*Option › Setup › TX › Radio command* でポートに **HRDPTT** を選びます。The Rigger は Ham Radio Deluxe として応答するので、PTT は The Rigger 経由になります。

### COM ポートしか使えないソフト（Windows）

Logger32、Win-Test、Winlink Express、SatPC32 は COM ポートしか使えません。Windows で COM ポートを作るには Microsoft が署名したドライバーが必要なため、いまのところ The Rigger ではこれらのソフトを使えません。代わりに次のソフトを使えます（どれも無料か、The Rigger とすでにつながるものです）：

| 代わりに | 使うソフト | 接続 |
|---|---|---|
| Logger32 | Log4OM 2、Swisslog、UcxLog、QLog、DXLab スイート | OmniRig、Hamlib、flrig、Thetis（Commander） |
| Win-Test | N1MM Logger+、DXLog.net、QARTest | ネットワーク CAT / TCI、OmniRig |
| Winlink Express | Pat Winlink、または無線機制御なしの Winlink Express（周波数は手動） | Hamlib |
| SatPC32 | Gpredict | Hamlib |

### 一覧にないソフト

ソフトが知っている接続を探してください：

- *Hamlib*、*NET rigctl*、*rigctld* があれば Hamlib（`127.0.0.1:4532`）；
- *FLRig* があれば flrig（`127.0.0.1:12345`）；
- *TCI* があれば TCI（`127.0.0.1:40001`）；
- *OmniRig*（Windows）があれば OmniRig の *Rig 1*；
- *Ham Radio Deluxe* があれば `127.0.0.1:7809`；
- TCP で無線機につなげるなら、実際の機種か Kenwood TS-2000 でネットワーク CAT（`127.0.0.1:4600`）；
- シリアルポートしか使えないなら（Mac と Linux）、`/tmp/TheRigger/` のポート。

## 複数の無線機を同時に

The Rigger はつないだ無線機をすべて扱います。各無線機には：

- 専用のアドレス（別のポート。*接続方法* の章の表を参照）；
- OmniRig と Ham Radio Deluxe 用の番号（**Rig 1**、**Rig 2**…）。「無線機」タブの順に、オンの無線機だけを数えます。

同じ機種が 2 台あれば、たとえば *IC-7300* と *IC-7300 2* という名前になります。

## The Rigger で無線機をオフにする

無線機カードの電源ボタンは、無線機を **The Rigger の中だけで** オフにします。USB ポートが空き、その無線機の接続が閉じます。メーカーのソフトやファームウェア更新など、別のソフトが無線機を直接使うときに使います。

この選択は再起動後も記憶されます。もう一度押すと無線機が戻ります。

## 設定

### 一般

- **言語**：*自動* はシステムの言語です。ほかにイタリア語、英語、フランス語、ドイツ語、スペイン語、ポルトガル語、日本語から選べます。ウィンドウ全体、マニュアル、ソフトの手順がすぐに切り替わります。
- **自動起動**：コンピューターの起動時に The Rigger が自動で開くので、ソフトより先に無線機の準備ができます。

### アップデート

- **自動アップデート**：起動のたびに新しいバージョンを確認します。あればダウンロードしてインストールし、数秒で自動的に再起動します。ソフトも自動で再接続します。
- **アップデートを確認**：すぐに確認します。下の行に状況が出ます（*最新バージョンです*、*アップデートをダウンロード中…*）。

ウィンドウの小さな修正は、再起動しなくてもすぐに届きます。

### ポートとドライバー

- **無線機ごとのシリアルポート数**（Mac と Linux）：無線機ごとに作る仮想ポートの数（1〜16）。すぐに反映されます。ソフトが使用中のポートは決して削除しません。
- **USB ドライバー自動導入**（Windows）：ドライバーのない無線機をつなぐと、The Rigger が公式ドライバーを入れます（*USB ドライバー* を参照）。

### 情報

バージョン、クレジット、PayPal で IU1MVI にコーヒーをごちそうするボタン。

## USB ドライバー

- **Windows**：ドライバーのない無線機をつなぐと、The Rigger が署名付きの公式ドライバー（Windows Update またはメーカーから）をダウンロードしてインストールします。Windows の確認は 1 回だけです。Silicon Labs CP210x（Icom、Yaesu、Kenwood）、FTDI（Elecraft と多くのケーブル）、WCH CH340（Xiegu と安価なケーブル）、Prolific に対応します。
- **macOS**：ドライバーはシステムに入っているので、何もいりません。

## 対応無線機

| メーカー | 機種 |
|---|---|
| Icom | IC-7100、IC-7300、IC-7300MK2、IC-705、IC-7610、IC-7760、IC-9700、IC-905、IC-7851、IC-7800、IC-7700、IC-7600、IC-7410、IC-7200、IC-7000、IC-9100、IC-746PRO、IC-7400、IC-756（全機種）、IC-718、IC-706（全機種）、IC-703、IC-910H などの CI-V 機、受信機 IC-R8600、IC-R75、IC-R30 |
| Xiegu | G90、X6100、X6200、X5105、X108G（Icom CI-V プロトコル） |
| Kenwood | TS-890S、TS-990S、TS-590S/SG、TS-2000、TS-480、TS-870S、TS-570、TS-850、TS-450S、TS-690S など CAT コマンドのある機種 |
| Elecraft | K3、K3S、K4、KX2、KX3 |
| Yaesu | FTX-1、FTDX10、FTDX101D/MP、FT-710、FT-991/991A、FT-891、FTDX3000、FTDX5000、FTDX1200、FT-950、FT-2000、FT-450/450D、FTDX9000 |
| Yaesu（旧機種） | FT-817、FT-818、FT-857、FT-897 |
| FlexRadio | SmartSDR の CAT ポート経由の 6000 シリーズ |
| Kenwood 互換 | Lab599 TX-500、QRP Labs QDX/QMX、(tr)uSDX、Malachite、多くの SDR |

メニューで CI-V アドレスを変えた Icom も見つかります。

## com0com のクリーンアップ (Windows)

### 何をするか

各手順を表示するウィンドウが開きます。仮想 COM ポートのペアを作る無料ドライバー com0com を探し、アンインストールし、すべての仮想ポート（デバイス マネージャーに表示されない「ゴースト」ポートも）を削除し、Windows からドライバーを削除し、それらのポートが占有していた COM 番号を解放します。何かを変更する前に見つかったものを表示して確認します (Y/N)。最後に再起動を提案します。

### なぜ使うのか

com0com は時間とともに数十〜数百の仮想ポートと予約済み COM 番号を残します。新しい USB ポートに非常に大きな番号が付き、Windows がエラーを繰り返し表示し、無線ソフトが混乱し、PC が遅くなります。The Rigger は仮想 COM ポートを使いません（ソフトは OmniRig、Hamlib、flrig、TCI、HRD、ネットワーク CAT で接続します。マニュアルを参照）。そのため com0com はもう必要ありません。

### リスク

管理者権限が必要です。com0com を使うソフトはそのポートで動かなくなります（たとえばポート分配ソフトや、仮想ポートでつないだ 2 つのソフト）。本物の COM ポート（無線機、USB シリアルケーブル）には触れません。元に戻せません。再び com0com が必要になったら再インストールしてください。先に COM ポートを使うソフトを閉じてください。自己責任で使用してください。作者は問題について責任を負いません。

### 使い方

**設定 → ポートとドライバー → com0com のクリーンアップ → クリーンアップ…**（ボタンは PC に com0com があるときだけ有効です）。注意書きを読み、*読んで理解しました* にチェックを入れて **クリーンアップを開始** を押します。Windows が管理者権限を求めます。開いたウィンドウで **Y** と答えて進め、最後に再起動するかを選び、Enter キーで閉じます。デバイスが残っていると表示された場合は、PC を再起動してもう一度実行してください。

## よくある問題

**無線機が出てこない。** 電源が入っていて USB ケーブルでつながっているか確認し、*無線機を再検索* を押してください。The Rigger より先にほかのソフトが無線機の USB ポートを開いていたら、そのソフトを閉じてください。ポートは The Rigger が持つ必要があります。Icom では *CI-V USB Baud Rate* を *Auto* か通常の値にしてください。

**Windows で無線機が出てこず、ドライバーがない。** *USB ドライバー自動導入* をオンのままにして、Windows の確認を許可してください。それでもだめなら、ケーブルのメーカーのドライバーを入れて *無線機を再検索* を押します。

**ソフトがつながらない。** このマニュアルで選んだ接続を確認し、アドレスを確認してください。次に無線機カードの *接続テスト* を押します。正確なアドレスが表示され、すべての行が ✓ なら The Rigger は正常で、問題はソフトの設定です。

**ソフトのランプが黄色。** ソフトは接続していますが、無線機に何も問い合わせていません。ソフトで CAT 制御が有効か確認してください（*Connect* や *Enable* ボタンがあることが多いです）。

**PTT が効かない。** ソフトの PTT を RTS や DTR ではなく **CAT**（または *PTT via Radio Command*）にしてください。

**OmniRig を使うソフトが「OmniRig がない」と言う。** このコンピューターで The Rigger を一度は開いている必要があります。The Rigger を開いてから、ソフトを開き直してください。

**ポートがほかのソフトに使われている。** flrig や rigctld などが同じポートを使っていると、The Rigger は次の空きポートを使います。*接続テスト* で正確なアドレスを確認してください。

**メーカーのソフトで無線機を使いたい。** 電源ボタンで The Rigger 内の無線機をオフにすると、USB ポートが空きます。

---

The Rigger · IU1MVI が開発したソフトウェア · すべてのアマチュア無線家が無料で自由に使えます。
OmniRig 互換機能は、Alex Shovkoplyas（VE3NEA）の OmniRig の公開インターフェース（MIT ライセンス）を使っています。Hamlib、flrig、TCI、Ham Radio Deluxe は各権利者の商標です。73!
