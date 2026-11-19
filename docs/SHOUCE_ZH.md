# The Rigger — 手册

## 简介

The Rigger 是唯一与电台通信的程序，并为每个程序提供各自的连接：WSJT-X、日志、比赛和 SDR 程序可以同时使用同一部电台。它会自动找到电台，可同时管理多部电台，并自动更新。它从不自行发射。

## 安装

**Windows**：下载 `The-Rigger-Windows.zip`，把 **The Rigger.exe** 放到你自己的文件夹（例如 *文档*）并打开。如果出现 *Windows 已保护你的电脑*：**更多信息 › 仍要运行**。不需要安装 OmniRig、com0com 或 Hamlib。桌面快捷方式会自动创建。

**Mac**：下载 `The-Rigger-Mac.pkg`（Apple 芯片）或 `The-Rigger-Mac-Intel.pkg`（Intel）并安装。如果 Mac 无法打开：*系统设置 › 隐私与安全性 › 仍要打开*。

## 首次启动

用 USB 线连接电台并开机：几秒钟后它会出现在 **电台** 标签页。The Rigger 里不需要任何设置。然后按下面的说明设置各个程序。

## 连接程序

所有方式都遵守三条规则：

- **PTT** 一律选 **CAT**（或 *通过电台命令 PTT*），不要用 RTS 或 DTR。
- 地址一律是 **127.0.0.1**（你自己的电脑）。
- 设置完成后，在程序中按 **Test**、**Connect** 或 **OK**。

选择你的程序支持的方式：

| 方式 | 设置内容 | 程序 |
|---|---|---|
| Hamlib | *Hamlib NET rigctl* · `127.0.0.1:4532` | WSJT-X, JTDX, JS8Call, MacLoggerDX, Gpredict, CQRLOG, VarAC |
| flrig | *FLRig* · `127.0.0.1` 端口 `12345` | fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog, Cloudlog) |
| TCI | *TCI* · `127.0.0.1:40001` | N1MM Logger+, MSHV, Log4OM, DXLog |
| OmniRig（Windows） | *OmniRig* · *Rig 1* | Log4OM, HDSDR, SDR Console, CW Skimmer, MMSSTV, UcxLog |
| Ham Radio Deluxe | 服务器 `127.0.0.1` 端口 `7809` | HRD Logbook, DM-780 |
| DXLab Commander | `127.0.0.1` 端口 `52002` | BBLogger |
| 网络 CAT | 真实型号或 *Kenwood TS-2000* · `127.0.0.1:4600` | N1MM Logger+, DXLab Commander（型号 *Thetis*） |
| 串口（Mac） | 真实型号 · 端口 `/tmp/TheRigger/…` · 任意速率 | RUMlogNG, SkookumLogger |

### Hamlib（WSJT-X 等）

1. **Rig**：*Hamlib NET rigctl*（有些程序叫 *rigctld*，型号 2）。
2. **服务器**：`127.0.0.1:4532`。
3. **PTT**：*CAT*。在 WSJT-X 中按 **Test CAT**：按钮变绿。

### flrig

1. 选择 **FLRig**（fldigi 中：*Rig Control › flrig › Connect to flrig*）。
2. 地址 `127.0.0.1`，端口 `12345`。不需要安装 flrig。

### TCI

1. 选择 **TCI**，地址 `127.0.0.1:40001`。
2. 音频照常走电台的声卡。

### OmniRig（仅 Windows）

1. 选择 **OmniRig**，然后选 **Rig 1**（第二部电台选 **Rig 2**）。不要安装真正的 OmniRig。
2. 正常启动程序，不要*以管理员身份运行*。

### Ham Radio Deluxe

1. 服务器 `127.0.0.1`，端口 `7809`，按 **Connect**。不需要打开 HRD Rig Control。
2. MMTTY 和 MMVARI：把免费插件 **HRDPTT.mmr** 复制到程序文件夹，端口选 **HRDPTT**。

### DXLab Commander（BBLogger）

1. 在 BBLogger 的 *Preferences › CAT* 中：**IP** `127.0.0.1`，**端口** `52002`，**Autostart** 留空。不需要 CatBKT。
2. 在 QSO 窗口按 **CAT ON**。

### 网络 CAT

1. 电台选 **真实型号**（例如 *IC-7100*）或 **Kenwood TS-2000**，连接选 **TCP**，`127.0.0.1` 端口 `4600`。
2. DXLab Commander：**Model** 选 *Thetis*，勾选 **Communicate via TCP**，`127.0.0.1` 端口 `4600`。

### 串口（Mac）

电台选 **真实型号** 或 **Kenwood TS-2000**，端口 `/tmp/TheRigger/IC-7100-1`（名称随电台而变），任意速率，无握手。每个程序用一个端口。

### N3FJP（Windows）

*Rig Interface*：**None**。*Application Program Interface*：勾选 **TCP API Enabled**，端口 `1100`。波段、模式和频率会自动填写。

### 第二部电台

| 方式 | 第一部电台 | 第二部电台 |
|---|---|---|
| Hamlib | 4532 | 4534 |
| flrig | 12345 | 12346 |
| TCI | 40001 | 40002 |
| DXLab Commander | 52002 | 52102 |
| 网络 CAT | 4600 | 4601 |
| OmniRig | Rig 1 | Rig 2 |
| Ham Radio Deluxe | 电台 1 | 电台 2（同一端口 7809） |

### 列表中没有的程序

在程序设置中按顺序查找以下选项：*Hamlib/rigctld*、*FLRig*、*TCI*、*OmniRig*、*Ham Radio Deluxe*、*TCP*。使用表格中对应的那一行。只支持 COM 端口的 Windows 程序（Logger32、Win-Test、SatPC32）无法连接：请改用 Log4OM、N1MM 或 Gpredict。

## 窗口

- **电台**：找到的电台，显示频率、模式和已连接的程序。卡片上的电源按钮会把电台让给其他程序（例如厂家软件）；真实电台不会关机。
- **手册**：本手册。
- **设置**：语言、开机自动启动、*隐藏启动*、更新、端口和驱动。

The Rigger 每次启动时都会自动更新。

## 仅 Windows

- **冲突的程序**：如果真正的 OmniRig、CatBKT、DXLab Commander、flrig、rigctld、HRD 或虚拟 COM 端口软件占用了电台或端口，电台标签页会出现一行黄色提示。**查看** 打开列表，可选 **关闭…**、**卸载…** 或 **清理…**（注册表中的 OmniRig 残留）。
- **com0com 清理**：*设置 › 端口和驱动 › 清理…* 删除 com0com 及其虚拟端口。阅读警告并确认，最后重启电脑。
- **USB 驱动**：如果缺少驱动，The Rigger 会自动安装官方驱动。

## 反馈和想法

右上角的对话气泡按钮：**出了问题** 或 **想法或需求**。附上最近一次启动的日志。反馈是匿名的；呼号可选。*查看实际发送的内容* 会在发送前显示全部内容。

## 常见问题

- **电台不出现**：开机、检查线缆，然后按 *重新搜索电台*。关闭直接打开电台 USB 端口的程序。
- **程序连不上**：对照表格重新检查方式和地址。如果程序在 The Rigger 之前就已打开，再按一次 *Test* 或 *Connect*。
- **PTT 不工作**：在程序中把 PTT 设为 **CAT**。
- **找不到 OmniRig**：至少打开一次 The Rigger，然后重新打开程序（不要以管理员身份）。

---

The Rigger · IU1MVI 开发的软件 · 对所有业余无线电爱好者免费。OmniRig 兼容功能使用 VE3NEA 的 OmniRig 公开接口（MIT 许可证）。Hamlib、flrig、TCI 和 Ham Radio Deluxe 是其各自所有者的商标。73!
