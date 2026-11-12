# The Rigger — 使用手册

## 它能做什么

The Rigger 是电台与电脑上各个程序之间的交换台。

通常，电台的 CAT 端口同一时间只能被一个程序使用：如果 WSJT-X 打开了它，日志软件就再也找不到电台。The Rigger 改变了这一点。只有 The Rigger 与电台通信，并为每个程序提供各自的连接。这样，WSJT-X、日志软件、比赛软件、CWIU1MVI、SDR 软件等都能在同一台电台上一起工作，互不干扰。

简而言之：

- **自动找到电台**：插上 USB 线，电台就会出现，无需选择端口、速率或型号；
- **同时支持多台电台**：每台都有自己的连接；
- **支持程序使用的所有连接方式**：Hamlib、flrig、TCI、OmniRig（Windows）、Ham Radio Deluxe、网络 CAT 和串口（Mac 和 Linux）；
- **自动更新**，支持 10 种语言。

The Rigger 从不自行发射，也从不更改电台上的任何设置：它只执行程序的请求。

## 安装

在 GitHub 项目（SculptWorksLTD/TheRigger）的 **Releases** 页面下载适合你系统的文件。

### Windows

1. 下载 `The-Rigger-…-Windows.zip`。
2. 打开 zip，把 **The Rigger.exe** 拖到你自己的文件夹，例如 *文档 › The Rigger*。不要把它留在 zip 里或临时的“下载”文件夹中。
3. 双击 **The Rigger.exe**。
4. 如果出现 *Windows 已保护你的电脑*，点击 **更多信息**，再点击 **仍要运行**。只有第一次会出现。

无需安装其他任何东西：不需要 OmniRig、com0com 或 Hamlib。

### macOS

1. 如果你的 Mac 是 Apple 芯片（M1、M2、M3、M4），下载 `The-Rigger-…-Mac.pkg`；Intel 芯片的 Mac 下载 `The-Rigger-…-Mac-Intel.pkg`。
2. 打开文件并按安装程序操作：The Rigger 会安装到 **应用程序**。
3. 如果 Mac 提示无法打开：右键点击文件 › **打开**，或 *系统设置 › 隐私与安全性 › 仍要打开*。

此后 The Rigger 会自动更新。

## 首次启动

启动时会出现带有作者信息的欢迎窗口：点击 **开始 · 73**。

用 USB 线连接电台并开机。几秒钟内 The Rigger 就会找到它：它会依次尝试 USB 端口、协议（Icom CI-V、Kenwood、Elecraft、Yaesu、FT-817）和速率，然后识别型号。你无需做任何设置。

电台出现在 **电台** 标签页中后即可使用：每个程序的设置方法见本手册的 **程序设置说明** 一章。

## 窗口

窗口有三个标签页，在顶部中间切换：

- **电台**：找到的电台，显示频率、模式和已连接的程序；
- **使用手册**：本手册，侧边有目录；
- **设置**：语言、启动、更新、端口和关于信息。

右上角有两个按钮：

- **隐藏**（向下箭头）：隐藏窗口。在 Mac 上，The Rigger 会留在菜单栏的时钟旁：点击图标并选择 *显示 The Rigger*。在 Windows 上，窗口会进入任务栏。
- **电源**（⏻）：退出 The Rigger。已连接的程序会失去电台，直到你再次打开它。

底部是状态栏：至少有一台电台连接时指示灯为绿色，有警告时为黄色。带圆形箭头的按钮会重新搜索电台。右侧显示版本号。

拖动窗口边缘可以调整大小。

## “电台”标签页

每台找到的电台都有自己的卡片。

### 标题栏

- **电源按钮**（左侧）：在 *The Rigger 内部* 开启或关闭电台。关闭时，The Rigger 会关闭其 USB 端口并释放出来，例如供厂家软件或固件升级使用。再按一次即可收回。真实的电台不会被关机。
- **名称**：型号；如果有两台相同的电台，会加上编号（例如 *IC-7300 2*）。
- **状态**：*已连接*（有响应）、*离线*（线已拔出或电台已关机）或 *关闭*（在 The Rigger 中关闭）。

### 显示屏

- 当前使用的 VFO 的 **频率**，以大号数字显示，旁边是 **模式**（USB、LSB、CW、CW-R、RTTY、AM、FM、USB-D、LSB-D、FM-D）。
- **A** 和 **B**：当前使用的 VFO。
- **SPLIT**：电台处于异频（split）状态时点亮。
- **TX**：电台发射时变红。
- 下方：另一个 VFO 的频率和 **S 表** 条。

无论你转动旋钮还是程序更改频率，显示屏都会实时跟随电台。

### 电台详情

灰色的一行显示型号、USB 端口、速率；如果电台在 The Rigger 中已开启，还显示它的编号（**Rig 1**、**Rig 2**…）。OmniRig 和 Ham Radio Deluxe 使用这个编号。

### 已连接的程序

使用这台电台的程序列表，每个都有一个指示灯：

- **绿色**：程序正在与电台通信；
- **黄色**：程序已连接，但此刻没有发出请求。

右侧是它使用的连接（例如 `tcp:4532`、`flrig`、`TCI`、某个串口）。点击即可复制地址。

### 按钮

- **测试连接**：模拟一个程序，通过每种连接（串口、Hamlib、flrig、网络 CAT、TCI）读取频率。带 **✓** 的行工作正常，带 **✗** 的行有问题。测试只读取：从不发射，也从不更改任何设置。

### 重新搜索电台

**重新搜索电台** 按钮（标签页右上角，或底部的圆形箭头）会立即重新检查所有 USB 端口。在打开了 The Rigger 没有发现的电台后，或关闭了占用端口的程序后使用。

## 连接方式

The Rigger 会同时为每台电台打开所有这些连接。每个程序使用它认识的那一种，多个程序也可以共用同一种连接。

| 连接方式 | 地址（第一台电台） | 第二台电台 | 系统 |
|---|---|---|---|
| Hamlib NET rigctl | 127.0.0.1:4532 | 127.0.0.1:4534 | 全部 |
| flrig | 127.0.0.1:12345 | 127.0.0.1:12346 | 全部 |
| TCI | 127.0.0.1:40001 | 127.0.0.1:40002 | 全部 |
| DXLab Commander | 127.0.0.1:52002 | 127.0.0.1:52102 | 全部 |
| 网络 CAT（Kenwood TS-2000） | 127.0.0.1:4600 | 127.0.0.1:4601 | 全部 |
| Ham Radio Deluxe | 127.0.0.1:7809（电台 1） | 同一端口，电台 2 | 全部 |
| OmniRig | Rig 1 | Rig 2 | Windows |
| 串口 | /tmp/TheRigger/… | /tmp/TheRigger/… | Mac 和 Linux |

如果某个端口已被其他程序占用（例如正在运行的真正 flrig 或 rigctld），The Rigger 会使用下一个空闲端口：在电台卡片上点击 *测试连接* 即可看到准确地址。

### Hamlib NET rigctl

供 WSJT-X、JTDX、JS8Call、FreeDV、Gpredict、CQRLOG、KLog、MacLoggerDX、Pat 以及所有使用 Hamlib 的程序使用。

在程序中选择 **Hamlib NET rigctl** 作为电台（有些程序中叫 *NET rigctl* 或 *rigctld*，Hamlib 型号编号 2），服务器填写显示的地址，例如 `127.0.0.1:4532`。PTT 设为 **CAT**。

### flrig

The Rigger 的响应与 flrig（W1HKJ）完全相同。供 fldigi、QLog、Not1MM、HAMRS、WaveLogGate（Wavelog 和 Cloudlog）、WFDlogger 以及所有带 *FLRig* 选项的程序使用。

在程序中选择 **FLRig**，地址 `127.0.0.1`，端口 `12345`（第二台电台 `12346`）。无需安装 flrig。

### TCI

The Rigger 的响应与 TCI 收发信机（Expert Electronics 协议）相同。N1MM Logger+、JTDX、MSHV、Log4OM、QLog、Swisslog、DXLog 等都在使用。

在程序中选择 **TCI**，地址 `127.0.0.1:40001`（第二台电台 `40002`）。The Rigger 的 TCI 传送频率、模式、PTT 和异频；音频仍像往常一样走电台的声卡。

### DXLab Commander（用于 BBLogger）

The Rigger 也能像 DXLab Commander 一样，用相同的网络消息应答。BBLogger 使用它；如有需要，WSJT-X、JTDX 和 MSHV 也可以选择电台 *DX Lab Suite Commander* 来使用。

地址 `127.0.0.1:52002`（第二台电台 `52102`）。支持频率、模式、PTT 和异频（split）。如果电脑上已经在运行真正的 DXLab Commander，52002 端口归它使用，The Rigger 不会占用。

### OmniRig（仅 Windows）

The Rigger 取代了 OmniRig：**无需安装 OmniRig**。在程序中选择 **OmniRig**，然后为 The Rigger 中第一台开启的电台选择 **Rig 1**，第二台选择 **Rig 2**。

适用于 Log4OM、DXLog.net、HDSDR、SDR Console、CW Skimmer、UcxLog、Swisslog、MixW、QARTest、VarAC 以及所有使用 OmniRig 的程序，32 位和 64 位都可以。如果某个程序在 The Rigger 关闭时请求 OmniRig，Windows 会在后台自动打开 The Rigger。

如果同时安装了真正的 OmniRig，程序仍然能找到 The Rigger，但 *以管理员身份* 启动的程序除外：请正常启动它们。不要在同一台电台上同时运行两者。

### Ham Radio Deluxe

The Rigger 的响应与 *HRD Rig Control* 相同。它服务于 HRD Logbook、DM-780 以及连接 Ham Radio Deluxe 的程序（包括选择 *Ham Radio Deluxe* 的 WSJT-X 和 JTDX）。

在程序中设置服务器 `127.0.0.1`，端口 `7809`。电台名称与 The Rigger 中相同，并按“电台”标签页中的顺序编号为 1、2、3…。

### 网络 CAT（TCP）

一个行为与电台串口相同的地址。适合能通过 TCP 连接电台的程序，例如 N1MM Logger+ 和 MSHV。

在程序中选择 **真实型号**（例如 *IC-7100*）或 **Kenwood TS-2000** 作为电台，端口填写显示的地址，例如 `127.0.0.1:4600`。PTT 设为 **CAT**。

### 串口（Mac 和 Linux）

对于一定要用串口的程序，The Rigger 会为每台电台创建几个虚拟串口，例如 `/tmp/TheRigger/IC-7100-1`、`/tmp/TheRigger/IC-7100-2`…

在程序中选择 **真实型号** 或 **Kenwood TS-2000** 作为电台，选择显示的端口，速率 **任意**，流控 **无**，PTT **CAT**。

每个端口会自动识别程序使用的协议：Icom CI-V、Kenwood、Elecraft、Yaesu、FT-817 或 TS-2000。如果选择真实型号，所有命令（包括特殊命令）都会送达电台。选择 TS-2000 时，频率、模式、PTT 和异频可以正常工作。

每个端口一个程序：The Rigger 为每个程序分配不同的端口。每台电台的端口数量可在设置中更改（1 到 16）。

在 Windows 上，The Rigger 不创建虚拟 COM 端口：请使用其他无需驱动的连接方式。

### CWIU1MVI

CWIU1MVI 会自动找到 The Rigger：在 CWIU1MVI 的电台列表中选择 **The Rigger · 电台名称**。无需其他设置。

## 程序设置说明

以下是最常用程序的设置步骤。地址均为第一台电台的地址：其他电台请见 *连接方式* 一章的表格。菜单名称按程序中显示的英文书写。

### WSJT-X、JTDX、JS8Call、WSJT-Z

1. *File › Settings › Radio*。
2. **Rig**：*Hamlib NET rigctl*。
3. **Network Server**：`127.0.0.1:4532`。
4. **PTT Method**：*CAT*。
5. **Mode**：如果希望电台处于 USB-D，选 *Data/Pkt*，否则选 *USB*。
6. **Split Operation**：*Rig* 或 *Fake It*，按你的习惯。
7. 点击 **Test CAT**：按钮变绿。然后点 **OK**。

### fldigi

1. *Configure › Config dialog › Rig Control › flrig*。
2. 勾选 **Connect to flrig**，地址 `127.0.0.1`，端口 `12345`。
3. 如果勾选了 *Hamlib* 和 *RigCAT*，请取消勾选。
4. **Save** 并关闭：fldigi 的频率会跟随电台。

### Log4OM 2（Windows）

1. *Settings › CAT interface*。
2. **CAT engine**：*OmniRig*。**Rig**：*Rig 1*（第二台电台选 *Rig 2*）。
3. 勾选 **Autostart** 并点击 **Connect**。

无需安装 OmniRig。也可以选择 *Hamlib* › *Connect to active HAMLIB interface*，端口 `4532`。

### N1MM Logger+（Windows）

1. *Config › Configure Ports, Mode Control, Winkey, etc… › Hardware*。
2. 在某个端口行选择 **TCP**，**Radio**：*IC-7100*（真实型号）或 *Kenwood TS-2000*。
3. 点击 **Set**，输入地址 `127.0.0.1`，端口 `4600`。
4. 开启 **PTT via Radio Command**。
5. **OK**：频率会显示在左下角。

N1MM 也可以使用 **TCI**，地址 `127.0.0.1:40001`。

### HRD Logbook 和 DM-780（Windows）

在电台连接窗口中选择服务器 `127.0.0.1`，端口 `7809`，然后点击 **Connect**。无需打开 *HRD Rig Control*：由 The Rigger 响应。

### QLog

1. *Settings › Equipment › Rig*，添加一台电台。
2. **Interface**：*FLRig*，主机 `127.0.0.1`，端口 `12345`（或 *Hamlib* › *NET rigctl*，地址 `127.0.0.1:4532`）。
3. 保存，然后从 *Equipment* 菜单连接电台。

### MacLoggerDX（Mac）

1. *Prefs › Radio*。
2. 选择 **Hamlib rigctld**，主机 `127.0.0.1`，端口 `4532`。
3. 在控制窗口中开启 **Radio VFO**。

也可以选择电台的真实型号，并使用 `/tmp/TheRigger/` 中的一个端口。

### RUMlogNG 和 SkookumLogger（Mac）

在电台偏好设置中选择 **真实型号**（或 Kenwood TS-2000），以及 `/tmp/TheRigger/` 中的一个端口，例如 `/tmp/TheRigger/IC-7100-2`，速率任意。

### Wavelog 和 Cloudlog（配合 WaveLogGate）

在 WaveLogGate 中打开 *Config › Radio*，选择 **FLRig**，主机 `127.0.0.1`，端口 `12345`，然后保存。Wavelog 会收到频率和模式，也能更改它们。

### HAMRS、Not1MM、WFDlogger

在电台控制设置中选择 **FLRig**，主机 `127.0.0.1`，端口 `12345`。

### MSHV

*Options › Radio and Network Configuration*：选择 **TCI**，地址 `127.0.0.1:40001`。

### HDSDR、SDR Console、CW Skimmer（Windows）

选择 **OmniRig**（HDSDR 中为 *Options › CAT to Radio (Omni-Rig)*，SDR Console 中为 *Radio › External Radio*，CW Skimmer 中为 *Setup › Radio*），然后选 **Rig 1**。

### Gpredict

*Edit › Preferences › Interfaces › Radios › Add new*：主机 `localhost`，端口 `4532`，类型选 *RX + TX* 或你需要的类型。

### CQRLOG（Linux）

*Preferences › TRX control*：取消勾选 *Run rigctld*，**Rig model**：*2 Hamlib NET rigctl*，**Device**：`127.0.0.1:4532`。

### VarAC（Windows）

*Settings › Rig control*：选择 **OmniRig** 和 *Rig 1*，或 **Hamlib (rigctld)**，地址 `127.0.0.1`，端口 `4532`。

### DXLab Commander（Windows）

Commander 不能使用 OmniRig 或 Hamlib，但可以通过网络与 Thetis 通信：The Rigger 的响应与 Thetis 相同。

1. *Config › Ports*，电台面板：**Model**：*Thetis*。
2. 勾选 **Communicate via TCP**，**IP Address** `127.0.0.1`，**IP Port** `4600`（第二台电台 `4601`）。
3. 关闭设置：Commander 会显示频率，DXKeeper、SpotCollector 和 DXLab 套件的其他程序也一样。

### N3FJP ACLog 和 N3FJP 比赛软件（Windows）

N3FJP 的程序没有 COM 端口就无法共用电台，但它们有网络接口：The Rigger 会自动通过它发送第一台开启电台的波段、模式和频率。

1. *Settings › Rig Interface*：选择 **None**。
2. *Settings › Application Program Interface*：勾选 **TCP API Enabled (Server)**，端口 `1100`。
3. 完成：波段、模式和频率会自动填写。The Rigger 从不替你记录 QSO。

这种方式下，ACLog 无法更改电台频率（例如点击某个 spot）。

### BBLogger（Windows）

BBLogger 本身不直接与电台通信，而是借助一个使用 DXLab Commander 消息的外部 CAT 程序。The Rigger 可以代替它，无需 CatBKT。

1. 在 BBLogger 中打开 *Strumenti › Configurazione/Manutenzione › Preferences*（或 CAT 设置）。
2. 在 **CAT** 区域保持 **IP** 为 `127.0.0.1`、**Porta** 为 `52002`（第二台电台 `52102`）。不需要点击 *Download*，也不需要安装 CatBKT。
3. **Autostart** 留空：The Rigger 已经在运行。
4. 关闭窗口：BBLogger 会显示电台的频率和模式，并可在 QSO 窗口中修改。
5. 在 QSO 窗口中按 **CAT ON**：Freq 和 Modo 标签会变成黄色。要自动开启，请勾选 *Strumenti › ABILITA CONNESSIONE CAT*。

如果 BBLogger 读不到频率，请关闭已打开的 CatBKT 或 DXLab Commander：它们占用了 52002 端口。

### MMSSTV、MMTTY 和 MMVARI（Windows）

- **MMSSTV**：*Option › Setup › TX › Radio command*，选择 **OmniRig** 和 *Rig 1*。
- **MMTTY 和 MMVARI**：下载免费插件 **HRDPTT.mmr**（它让 MM 系列程序能与 Ham Radio Deluxe 通信），复制到程序文件夹，然后在 *Option › Setup › TX › Radio command* 中选择 **HRDPTT** 作为端口。The Rigger 的响应与 Ham Radio Deluxe 相同，因此 PTT 会经过 The Rigger。

### 只接受 COM 端口的程序（Windows）

Logger32、Win-Test、Winlink Express 和 SatPC32 只认 COM 端口，而在 Windows 上这需要经过微软签名的驱动：目前 The Rigger 还不能与这些程序一起使用。以下是替代方案，全部免费或已可与 The Rigger 配合使用：

| 替代 | 改用 | 连接方式 |
|---|---|---|
| Logger32 | Log4OM 2、Swisslog、UcxLog、QLog 或 DXLab 套件 | OmniRig、Hamlib、flrig 或 Thetis（Commander） |
| Win-Test | N1MM Logger+、DXLog.net 或 QARTest | 网络 CAT / TCI、OmniRig |
| Winlink Express | Pat Winlink，或不控制电台的 Winlink Express（手动设置频率） | Hamlib |
| SatPC32 | Gpredict | Hamlib |

### 未列出的程序

看看程序支持哪种连接方式：

- 如果有 *Hamlib*、*NET rigctl* 或 *rigctld*，使用 Hamlib（`127.0.0.1:4532`）；
- 如果有 *FLRig*，使用 flrig（`127.0.0.1:12345`）；
- 如果有 *TCI*，使用 TCI（`127.0.0.1:40001`）；
- 如果有 *OmniRig*（Windows），使用 OmniRig *Rig 1*；
- 如果有 *Ham Radio Deluxe*，使用 `127.0.0.1:7809`；
- 如果它通过 TCP 连接电台，使用网络 CAT（`127.0.0.1:4600`），选择真实型号或 Kenwood TS-2000；
- 如果它只接受串口（Mac 和 Linux），使用 `/tmp/TheRigger/` 中的端口。

## 同时使用多台电台

The Rigger 管理你连接的每一台电台。每台电台都有：

- 自己的地址（不同的端口，见 *连接方式* 一章的表格）；
- 自己的编号（**Rig 1**、**Rig 2**…），供 OmniRig 和 Ham Radio Deluxe 使用，按“电台”标签页中的顺序排列，只计算已开启的电台。

如果有两台同型号的电台，它们会被命名为例如 *IC-7300* 和 *IC-7300 2*。

## 在 The Rigger 中关闭电台

电台卡片上的电源按钮 **只在 The Rigger 内部** 关闭电台：USB 端口被释放，该电台的连接全部关闭。当其他程序需要直接使用电台时（例如厂家软件或固件升级）使用此功能。

The Rigger 在重启后也会记住这个选择。再按一次按钮即可收回电台。

## 设置

### 常规

- **语言**：*自动* 使用系统语言；也可以选择意大利语、英语、法语、德语、西班牙语、葡萄牙语、日语、俄语、阿拉伯语或中文。整个窗口、手册和程序设置说明会立即切换。
- **开机自动启动**：电脑开机时 The Rigger 自动打开，电台会比程序先准备好。

### 更新

- **自动更新**：每次启动时 The Rigger 都会检查是否有新版本。如果有，它会下载、安装，并在几秒钟内自动重启；程序会自动重新连接。
- **检查更新**：立即检查。下方一行显示当前状态（*你已是最新版本*、*正在下载更新…*）。

窗口的小修复会即时生效，甚至无需重启。

### 端口和驱动

- **每台电台的串口数**（Mac 和 Linux）：为每台电台创建多少个虚拟串口，1 到 16。立即生效；正在被程序使用的端口不会被删除。
- **自动安装 USB 驱动**（Windows）：如果连接了没有驱动的电台，The Rigger 会安装官方驱动（见 *USB 驱动*）。

### 关于

版本、作者信息，以及通过 PayPal 请 IU1MVI 喝杯咖啡的按钮。

## USB 驱动

- **Windows**：如果连接了没有驱动的电台，The Rigger 会下载官方签名驱动（来自 Windows Update 或厂家）并安装。Windows 只会请求一次确认。支持 Silicon Labs CP210x（Icom、Yaesu、Kenwood）、FTDI（Elecraft 和许多数据线）、WCH CH340（Xiegu 和廉价数据线）以及 Prolific。
- **macOS**：系统已自带驱动，无需任何操作。

## 支持的电台

| 品牌 | 型号 |
|---|---|
| Icom | IC-7100、IC-7300、IC-7300MK2、IC-705、IC-7610、IC-7760、IC-9700、IC-905、IC-7851、IC-7800、IC-7700、IC-7600、IC-7410、IC-7200、IC-7000、IC-9100、IC-746PRO、IC-7400、IC-756（全部）、IC-718、IC-706（全部）、IC-703、IC-910H 及其他 CI-V 电台，接收机 IC-R8600、IC-R75、IC-R30 |
| Xiegu | G90、X6100、X6200、X5105、X108G（Icom CI-V 协议） |
| Kenwood | TS-890S、TS-990S、TS-590S/SG、TS-2000、TS-480、TS-870S、TS-570、TS-850、TS-450S、TS-690S 及其他支持 CAT 命令的电台 |
| Elecraft | K3、K3S、K4、KX2、KX3 |
| Yaesu | FTX-1、FTDX10、FTDX101D/MP、FT-710、FT-991/991A、FT-891、FTDX3000、FTDX5000、FTDX1200、FT-950、FT-2000、FT-450/450D、FTDX9000 |
| Yaesu 经典机型 | FT-817、FT-818、FT-857、FT-897 |
| FlexRadio | 6000 系列，通过 SmartSDR 的 CAT 端口 |
| 兼容 Kenwood | Lab599 TX-500、QRP Labs QDX/QMX、(tr)uSDX、Malachite 以及许多 SDR |

即使在菜单中更改过 CI-V 地址的 Icom 电台也能被找到。

## 冲突的程序（Windows）

有些程序和 The Rigger 做同样的事，如果它们正在运行或已安装，就会抢走电台，或占用其他程序寻找 The Rigger 的端口：真正的 OmniRig、CatBKT、DXLab Commander、flrig、Hamlib rigctld、Ham Radio Deluxe，以及创建虚拟 COM 端口的程序（VSPE、Virtual Serial Port Driver）。The Rigger 每 20 秒自动查找一次。

如果找到，**电台**选项卡会出现一行带 **查看** 链接的黄色提示，点击进入 **设置 › 端口和驱动 › 冲突的程序**。每个程序都会显示它是正在运行还是已安装、会造成什么问题，并有两个按钮：

- **关闭…**：立即关闭，不卸载任何东西；
- **卸载…**：打开它的卸载程序（Windows 会请求管理员权限）。

每次操作前都会有窗口说明会发生什么、原因和风险；只有勾选 *我已阅读并理解* 才能继续。之后 The Rigger 会自动接管空出来的电台和端口。DXLab Commander、rigctld 和 Ham Radio Deluxe 只能关闭：它们属于更大的软件包，你可能想保留。

## com0com 清理（Windows）

### 它会做什么

每一步都会显示在 The Rigger 窗口中。它会查找 com0com（一个创建成对虚拟 COM 端口的免费驱动），然后：卸载它，删除它的所有虚拟端口（包括设备管理器中看不到的“幽灵”端口），从 Windows 中删除它的驱动，并释放这些端口占用的 COM 编号。在做任何更改之前，它会显示找到的内容并请求确认；最后会建议重启。

### 为什么要用

随着时间推移，com0com 会留下几十甚至几百个虚拟端口和被保留的 COM 编号：新的 USB 端口会得到很大的编号，Windows 不断报错，电台软件会混乱，电脑也会变慢。The Rigger 不使用虚拟 COM 端口（各程序通过 OmniRig、Hamlib、flrig、TCI、HRD 或网络 CAT 连接，见使用手册），因此不再需要 com0com。

### 风险

需要管理员权限。使用 com0com 的程序将无法再使用这些端口，例如端口分配器，或通过虚拟端口相连的两个程序。真实的 COM 端口（电台、USB 转串口线）不受影响。此操作无法撤销：如果以后还需要 com0com，必须重新安装。请先关闭使用 COM 端口的程序。使用风险自负：作者对任何问题不承担责任。

### 使用方法

**设置 → 端口和驱动 → com0com 清理 → 清理…**（只有电脑上有 com0com 时按钮才可用）。阅读警告，勾选 *我已阅读并理解*，然后点击 **开始清理**。Windows 会请求管理员权限：选择 **是**。各步骤会显示在同一个 The Rigger 窗口中；搜索完成后点击 **继续**（或点击 **取消** 保持原样）。最后可以点击 **立即重启** 或 **关闭**。如果窗口提示仍有设备残留，请重启电脑并再次运行清理。

## 问题报告与想法

右上角的对话气泡按钮可以让你免费、匿名地报告问题或提出想法。

- **出了问题**：写下你当时在做什么、预期是什么、实际发生了什么，并注明电台和程序。通常附上 **最近一次启动** 的日志；如果问题时有时无，附上 **最近 7 天** 的日志。
- **想法或需求**：新功能、要连接的程序、要添加的电台。每个想法都会被评估；对多数人有用的会加入后续版本。

**匿名性。** 我们不会发送你的姓名、呼号、邮箱或 IP 地址。发送前，The Rigger 会从日志中删除用户名、电脑名、个人文件夹和网络地址。点击 *查看实际发送的内容* 可以逐字检查离开你电脑的内容。请不要在文字中填写个人信息。

日志是 The Rigger 保存在你电脑上的文本文件（最近 12 次启动）；只有你选择时才会发送。

**呼号。** 顶部有一个可选的呼号栏：填写后我们可以联系你了解详情；留空则报告完全匿名。The Rigger 会记住它，下次自动填入。

## 故障排除

**电台没有出现。** 检查电台是否已开机并用 USB 线连接，然后点击 *重新搜索电台*。如果有其他程序在 The Rigger 之前打开了电台的 USB 端口，请关闭它：端口必须归 The Rigger 所有。Icom 电台的 *CI-V USB Baud Rate* 应设为 *Auto* 或常规数值。

**在 Windows 上电台没有出现且缺少驱动。** 保持 *自动安装 USB 驱动* 开启，并确认 Windows 的请求。如果仍不行，请安装数据线厂家的驱动，然后点击 *重新搜索电台*。

**程序连接不上。** 对照本手册检查是否选对了连接方式和地址。然后在电台卡片上点击 *测试连接*：它会显示准确的地址；如果每一行都是 ✓，说明 The Rigger 工作正常，问题出在程序的设置上。

**程序的指示灯是黄色。** 程序已连接，但没有向电台发出请求。检查程序中是否启用了 CAT 控制（通常有 *Connect* 或 *Enable* 按钮）。

**PTT 不工作。** 程序中的 PTT 必须设为 **CAT**（或 *PTT via Radio Command*），而不是 RTS 或 DTR。

**使用 OmniRig 的程序提示找不到 OmniRig。** The Rigger 必须在这台电脑上至少打开过一次。打开它，然后重新打开该程序。

**端口已被其他程序占用。** 如果 flrig、rigctld 或其他程序占用了相同的端口，The Rigger 会使用下一个空闲端口：用 *测试连接* 查看准确地址。

**我想用厂家软件操作电台。** 用电台卡片上的电源按钮在 The Rigger 中关闭电台：USB 端口就会被释放。

---

The Rigger · 本软件由 IU1MVI 开发 · 所有业余无线电爱好者均可免费自由使用。
OmniRig 兼容功能使用了 Alex Shovkoplyas（VE3NEA）开发的 OmniRig 的公开接口（MIT 许可）。Hamlib、flrig、TCI 和 Ham Radio Deluxe 是其各自所有者的商标。73！
