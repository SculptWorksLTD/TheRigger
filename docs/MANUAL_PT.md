# The Rigger — Manual

## O que faz

O The Rigger funciona como central entre os seus rádios e os programas do computador.

Normalmente a porta CAT de um rádio só pode ser usada por um programa de cada vez: se o WSJT-X a abre, o livro de registo deixa de a encontrar. Com o The Rigger é diferente. O The Rigger é o único que fala com o rádio e dá a cada programa uma ligação própria. Assim o WSJT-X, o livro de registo, o programa de concursos, o CWIU1MVI, o programa SDR e os outros trabalham juntos no mesmo rádio sem se incomodarem.

Em resumo:

- **encontra os rádios sozinho**: liga o cabo USB e o rádio aparece, sem escolher porta, velocidade nem modelo;
- **vários rádios ao mesmo tempo**: cada um tem as suas ligações;
- **todas as ligações que os programas usam**: Hamlib, flrig, TCI, OmniRig (Windows), Ham Radio Deluxe, CAT em rede e portas série (Mac e Linux);
- **atualiza-se sozinho** e fala 7 línguas.

O The Rigger nunca transmite por iniciativa própria nem muda nada no rádio: só faz o que os programas pedem.

## Instalação

Descarregue o ficheiro do seu sistema na página **Releases** do projeto no GitHub (SculptWorksLTD/TheRigger).

### Windows

1. Descarregue `The-Rigger-…-Windows.zip`.
2. Abra o zip e arraste **The Rigger.exe** para uma pasta sua, por exemplo *Documentos › The Rigger*. Não o deixe dentro do zip nem numa pasta de transferências temporária.
3. Faça duplo clique em **The Rigger.exe**.
4. Se aparecer *O Windows protegeu o seu PC*, clique em **Mais informações** e depois em **Executar mesmo assim**. Só acontece da primeira vez.

Não é preciso instalar mais nada: nem OmniRig, nem com0com, nem Hamlib.

### macOS

1. Descarregue `The-Rigger-…-Mac.pkg` se o seu Mac tem chip Apple (M1, M2, M3, M4), ou `The-Rigger-…-Mac-Intel.pkg` para um Mac Intel.
2. Abra o ficheiro e siga a instalação: o The Rigger fica em **Aplicações**.
3. Se o Mac não o abrir: clique com o botão direito no ficheiro › **Abrir**, ou *Definições do Sistema › Privacidade e segurança › Abrir mesmo assim*.

A partir daí o The Rigger atualiza-se sozinho.

## Primeiro arranque

No arranque aparece a janela de boas-vindas com os créditos: carregue em **Começar · 73**.

Ligue o rádio com o cabo USB e ligue-o. Em poucos segundos o The Rigger encontra-o: experimenta as portas USB, o protocolo (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817) e a velocidade, e reconhece o modelo. Não tem de configurar nada.

Quando o rádio aparecer no separador **Rádios** está pronto: para configurar cada programa veja o capítulo **Instruções para os programas** deste manual.

## A janela

A janela tem três separadores, em cima ao centro:

- **Rádios**: os rádios encontrados, com frequência, modo, programas ligados e endereços;
- **Manual**: este manual, com o índice à esquerda;
- **Definições**: idioma, arranque, atualizações, portas e informações.

Em cima à direita há dois botões:

- **Ocultar** (seta para baixo): esconde a janela. No Mac o The Rigger fica na barra de menus, perto do relógio: clique no ícone e escolha *Mostrar The Rigger*. No Windows a janela vai para a barra de tarefas.
- **Desligar** (⏻): fecha o The Rigger. Os programas ligados perdem o rádio até o abrir de novo.

Em baixo está a barra de estado: a luz fica verde quando há pelo menos um rádio ligado e amarela quando há um aviso. O botão com a seta circular procura os rádios de novo. A versão está à direita.

Pode mudar o tamanho da janela arrastando as margens.

## Separador Rádios

Cada rádio encontrado tem a sua ficha.

### Cabeçalho

- **Botão de ligar** (à esquerda): liga ou desliga o rádio *dentro do The Rigger*. Desligado, o The Rigger fecha a sua porta USB e deixa-a livre, por exemplo para o programa do fabricante ou uma atualização de firmware. Carregue de novo para o recuperar. O rádio verdadeiro não se desliga.
- **Nome**: o modelo, com um número se tiver dois rádios iguais (por exemplo *IC-7300 2*).
- **Estado**: *ligado* (responde), *desligado* (cabo tirado ou rádio desligado) ou *desligada* no The Rigger.

### Visor

- **Frequência** do VFO em uso, em grande, com o **modo** ao lado (USB, LSB, CW, CW-R, RTTY, AM, FM, USB-D, LSB-D, FM-D).
- **A** e **B**: que VFO está em uso.
- **SPLIT**: aceso quando o rádio está em split.
- **TX**: fica vermelho quando o rádio transmite.
- Por baixo: a frequência do outro VFO e a barra do **S-meter**.

O visor segue o rádio em tempo real, tanto ao rodar o botão como quando um programa muda a frequência.

### Dados do rádio

A linha cinzenta mostra modelo, porta USB, velocidade e, se o rádio estiver ligado no The Rigger, o seu número (**Rig 1**, **Rig 2**…). Esse número é usado pelo OmniRig e pelo Ham Radio Deluxe.

### Programas ligados

A lista dos programas que usam este rádio, cada um com uma luz:

- **verde**: o programa está a falar com o rádio;
- **amarela**: o programa está ligado mas agora não pede nada.

À direita está a ligação que usa (por exemplo `tcp:4532`, `flrig`, `TCI`, uma porta série). Clique para copiar o endereço.

### Endereços para os programas

Todas as maneiras de um programa se ligar a este rádio, com o endereço a escrever no programa. Clique num endereço para o copiar. As explicações estão no capítulo **As ligações**.

### Botões

- **Testar ligação**: faz de conta que é um programa e lê a frequência por cada ligação (porta série, Hamlib, flrig, CAT em rede, TCI). Cada linha com **✓** funciona, cada linha com **✗** tem um problema. O teste só lê: nunca transmite nem muda nada.

### Procurar rádios de novo

O botão **Procurar rádios de novo** (em cima à direita do separador, ou a seta circular em baixo) volta a verificar todas as portas USB de imediato. Use-o depois de ligar um rádio que o The Rigger não via, ou depois de fechar um programa que tinha a porta ocupada.

## As ligações

O The Rigger abre todas estas ligações para cada rádio ao mesmo tempo. Cada programa usa a que conhece, e vários programas podem partilhar a mesma ligação.

| Ligação | Endereço (primeiro rádio) | Segundo rádio | Sistemas |
|---|---|---|---|
| Hamlib NET rigctl | 127.0.0.1:4532 | 127.0.0.1:4534 | todos |
| flrig | 127.0.0.1:12345 | 127.0.0.1:12346 | todos |
| TCI | 127.0.0.1:40001 | 127.0.0.1:40002 | todos |
| CAT em rede (Kenwood TS-2000) | 127.0.0.1:4600 | 127.0.0.1:4601 | todos |
| Ham Radio Deluxe | 127.0.0.1:7809 (rádio 1) | mesma porta, rádio 2 | todos |
| OmniRig | Rig 1 | Rig 2 | Windows |
| Portas série | /tmp/TheRigger/… | /tmp/TheRigger/… | Mac e Linux |

Se uma porta já estiver ocupada por outro programa (por exemplo um flrig ou rigctld verdadeiros já abertos), o The Rigger usa a seguinte livre: o endereço exato está sempre no separador Rádios.

### Hamlib NET rigctl

É a ligação do WSJT-X, JTDX, JS8Call, FreeDV, Gpredict, CQRLOG, KLog, MacLoggerDX, Pat e de todos os programas que usam o Hamlib.

No programa escolha como rádio **Hamlib NET rigctl** (em alguns programas *NET rigctl* ou *rigctld*, modelo Hamlib número 2) e como servidor o endereço indicado, por exemplo `127.0.0.1:4532`. PTT em **CAT**.

### flrig

O The Rigger responde exatamente como o flrig (W1HKJ). É a ligação do fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog e Cloudlog), WFDlogger e de todos os programas com a opção *FLRig*.

No programa escolha **FLRig**, endereço `127.0.0.1` e porta `12345` (segundo rádio `12346`). Não é preciso instalar o flrig.

### TCI

O The Rigger responde como um equipamento TCI (o protocolo da Expert Electronics). É usado pelo N1MM Logger+, JTDX, MSHV, Log4OM, QLog, Swisslog, DXLog e outros.

No programa escolha **TCI** e o endereço `127.0.0.1:40001` (segundo rádio `40002`). O TCI do The Rigger transporta frequências, modo, PTT e split; o áudio continua na placa de som do rádio, como sempre.

### OmniRig (só Windows)

O The Rigger ocupa o lugar do OmniRig: **não é preciso instalar o OmniRig**. No programa escolha **OmniRig** e depois **Rig 1** para o primeiro rádio ligado no The Rigger ou **Rig 2** para o segundo.

Funciona com Log4OM, DXLog.net, HDSDR, SDR Console, CW Skimmer, UcxLog, Swisslog, MixW, QARTest, VarAC e com todos os programas que usam o OmniRig, de 32 ou 64 bits. Se um programa pedir o OmniRig com o The Rigger fechado, o Windows abre o The Rigger sozinho, oculto.

Se também tiver o OmniRig verdadeiro instalado, os programas encontram mesmo assim o The Rigger, exceto os iniciados *como administrador*: inicie-os normalmente. Não deixe os dois abertos ao mesmo tempo no mesmo rádio.

### Ham Radio Deluxe

O The Rigger responde como o *HRD Rig Control*. Serve o HRD Logbook, o DM-780 e os programas que se ligam ao Ham Radio Deluxe (também o WSJT-X e o JTDX com a opção *Ham Radio Deluxe*).

No programa configure o servidor `127.0.0.1` porta `7809`. Os rádios têm os mesmos nomes que no The Rigger e estão numerados 1, 2, 3… pela ordem do separador Rádios.

### CAT em rede (TCP)

Um endereço que se comporta como a porta série do rádio. Serve os programas que sabem ligar-se a um rádio por TCP, como o N1MM Logger+ e o MSHV.

No programa escolha como rádio **o modelo verdadeiro** (por exemplo *IC-7100*) ou **Kenwood TS-2000**, e como porta o endereço indicado, por exemplo `127.0.0.1:4600`. PTT em **CAT**.

### Portas série (Mac e Linux)

Para os programas que exigem uma porta série, o The Rigger cria algumas portas virtuais para cada rádio, por exemplo `/tmp/TheRigger/IC-7100-1`, `/tmp/TheRigger/IC-7100-2`…

No programa escolha o **modelo verdadeiro** ou **Kenwood TS-2000**, a porta indicada, velocidade **qualquer**, controlo de fluxo **nenhum**, PTT **CAT**.

Cada porta reconhece sozinha a linguagem do programa: Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 ou TS-2000. Com o modelo verdadeiro chegam ao rádio todos os comandos, mesmo os especiais. Com TS-2000 funcionam frequência, modo, PTT e split.

Um programa por porta: o The Rigger dá a cada programa uma porta diferente. O número de portas por rádio muda-se nas Definições (de 1 a 16).

No Windows o The Rigger não cria portas COM virtuais: use as outras ligações, que não precisam de drivers.

### CWIU1MVI

O CWIU1MVI encontra o The Rigger sozinho: na lista de rádios do CWIU1MVI escolha **The Rigger · nome do rádio**. Não há mais nada a configurar.

## Instruções para os programas

Aqui estão os passos para os programas mais usados. Os endereços são os do primeiro rádio: para os outros, copie-os do separador Rádios.

### WSJT-X, JTDX, JS8Call, WSJT-Z

1. *File › Settings › Radio*.
2. **Rig**: *Hamlib NET rigctl*.
3. **Network Server**: `127.0.0.1:4532`.
4. **PTT Method**: *CAT*.
5. **Mode**: *Data/Pkt* se quiser o rádio em USB-D, senão *USB*.
6. **Split Operation**: *Rig* ou *Fake It*, como preferir.
7. Carregue em **Test CAT**: fica verde. Depois **OK**.

### fldigi

1. *Configure › Config dialog › Rig Control › flrig*.
2. Marque **Connect to flrig**, endereço `127.0.0.1`, porta `12345`.
3. Desmarque *Hamlib* e *RigCAT* se estiverem marcados.
4. **Save** e feche: a frequência do fldigi segue o rádio.

### Log4OM 2 (Windows)

1. *Settings › CAT interface*.
2. **CAT engine**: *OmniRig*. **Rig**: *Rig 1* (ou *Rig 2* para o segundo rádio).
3. Marque **Autostart** e carregue em **Connect**.

Não é preciso instalar o OmniRig. Em alternativa escolha *Hamlib* › *Connect to active HAMLIB interface* com a porta `4532`.

### N1MM Logger+ (Windows)

1. *Config › Configure Ports, Mode Control, Winkey, etc… › Hardware*.
2. Numa linha de porta escolha **TCP**, **Radio**: *IC-7100* (o modelo verdadeiro) ou *Kenwood TS-2000*.
3. Carregue em **Set** e escreva o endereço `127.0.0.1` porta `4600`.
4. Ative **PTT via Radio Command**.
5. **OK**: a frequência aparece em baixo à esquerda.

Em alternativa o N1MM pode usar **TCI** com `127.0.0.1:40001`.

### HRD Logbook e DM-780 (Windows)

Na janela de ligação ao rádio escolha o servidor `127.0.0.1` porta `7809` e carregue em **Connect**. Não é preciso abrir o *HRD Rig Control*: responde o The Rigger.

### QLog

1. *Settings › Equipment › Rig*, adicione um rádio.
2. **Interface**: *FLRig*, host `127.0.0.1`, porta `12345` (ou *Hamlib* › *NET rigctl* com `127.0.0.1:4532`).
3. Guarde e ligue o rádio no menu *Equipment*.

### MacLoggerDX (Mac)

1. *Prefs › Radio*.
2. Escolha **Hamlib rigctld**, host `127.0.0.1`, porta `4532`.
3. Ative **Radio VFO** na janela de controlo.

Em alternativa escolha o modelo verdadeiro do rádio e uma porta de `/tmp/TheRigger/`.

### RUMlogNG e SkookumLogger (Mac)

Nas preferências do rádio escolha o **modelo verdadeiro** (ou Kenwood TS-2000) e uma porta de `/tmp/TheRigger/`, por exemplo `/tmp/TheRigger/IC-7100-2`, velocidade qualquer.

### Wavelog e Cloudlog (com o WaveLogGate)

No WaveLogGate abra *Config › Radio*, escolha **FLRig**, host `127.0.0.1`, porta `12345`, e guarde. O Wavelog recebe frequência e modo e pode mudá-los.

### HAMRS, Not1MM, WFDlogger

Nas definições de controlo do rádio escolha **FLRig**, host `127.0.0.1`, porta `12345`.

### MSHV

*Options › Radio and Network Configuration*: escolha **TCI** e o endereço `127.0.0.1:40001`.

### HDSDR, SDR Console, CW Skimmer (Windows)

Escolha **OmniRig** (no HDSDR *Options › CAT to Radio (Omni-Rig)*, no SDR Console *Radio › External Radio*, no CW Skimmer *Setup › Radio*) e depois **Rig 1**.

### Gpredict

*Edit › Preferences › Interfaces › Radios › Add new*: host `localhost`, porta `4532`, tipo *RX + TX* ou o que precisar.

### CQRLOG (Linux)

*Preferences › TRX control*: desmarque *Run rigctld*, **Rig model**: *2 Hamlib NET rigctl*, **Device**: `127.0.0.1:4532`.

### VarAC (Windows)

*Settings › Rig control*: escolha **OmniRig** e *Rig 1*, ou **Hamlib (rigctld)** com `127.0.0.1` porta `4532`.

### DXLab Commander (Windows)

O Commander não sabe usar o OmniRig nem o Hamlib, mas sabe falar em rede com o Thetis: o The Rigger responde como o Thetis.

1. *Config › Ports*, painel do rádio: **Model**: *Thetis*.
2. Marque **Communicate via TCP**, **IP Address** `127.0.0.1`, **IP Port** `4600` (segundo rádio `4601`).
3. Feche a configuração: o Commander mostra a frequência, e com ele o DXKeeper, o SpotCollector e o resto da suite DXLab.

### N3FJP ACLog e programas de concursos N3FJP (Windows)

Os programas N3FJP não sabem partilhar um rádio sem porta COM, mas têm uma interface de rede: o The Rigger usa-a sozinho para enviar banda, modo e frequência do primeiro rádio ligado.

1. *Settings › Rig Interface*: escolha **None**.
2. *Settings › Application Program Interface*: marque **TCP API Enabled (Server)**, porta `1100`.
3. Pronto: banda, modo e frequência preenchem-se sozinhos. O The Rigger nunca regista QSO por si.

Assim o ACLog não pode mudar a frequência do rádio (por exemplo ao clicar num spot).

### MMSSTV, MMTTY e MMVARI (Windows)

- **MMSSTV**: *Option › Setup › TX › Radio command*, escolha **OmniRig** e *Rig 1*.
- **MMTTY e MMVARI**: descarregue o plugin gratuito **HRDPTT.mmr** (faz os programas MM falarem com o Ham Radio Deluxe), copie-o para a pasta do programa, depois *Option › Setup › TX › Radio command* e escolha **HRDPTT** como porta. O The Rigger responde como o Ham Radio Deluxe, por isso o PTT passa pelo The Rigger.

### Programas que só querem uma porta COM (Windows)

O Logger32, o Win-Test, o Winlink Express e o SatPC32 só conhecem portas COM, que no Windows precisam de um driver assinado pela Microsoft: por agora o The Rigger não pode ser usado com estes programas. Eis o que pode usar em vez deles, tudo gratuito ou já compatível com o The Rigger:

| Em vez de | Use | Ligação |
|---|---|---|
| Logger32 | Log4OM 2, Swisslog, UcxLog, QLog ou a suite DXLab | OmniRig, Hamlib, flrig ou Thetis (Commander) |
| Win-Test | N1MM Logger+, DXLog.net ou QARTest | CAT em rede / TCI, OmniRig |
| Winlink Express | Pat Winlink, ou o Winlink Express sem controlo do rádio (frequência à mão) | Hamlib |
| SatPC32 | Gpredict | Hamlib |

### Programas que não estão na lista

Veja que ligação o programa conhece:

- se tem *Hamlib*, *NET rigctl* ou *rigctld*, use Hamlib (`127.0.0.1:4532`);
- se tem *FLRig*, use flrig (`127.0.0.1:12345`);
- se tem *TCI*, use TCI (`127.0.0.1:40001`);
- se tem *OmniRig* (Windows), use OmniRig *Rig 1*;
- se tem *Ham Radio Deluxe*, use `127.0.0.1:7809`;
- se se liga a um rádio por TCP, use o CAT em rede (`127.0.0.1:4600`) com o modelo verdadeiro ou Kenwood TS-2000;
- se só quer uma porta série (Mac e Linux), use uma porta de `/tmp/TheRigger/`.

## Vários rádios ao mesmo tempo

O The Rigger gere todos os rádios que ligar. Cada rádio tem:

- os seus endereços (portas diferentes, veja a tabela do capítulo *As ligações*);
- o seu número (**Rig 1**, **Rig 2**…) para o OmniRig e o Ham Radio Deluxe, pela ordem do separador Rádios, contando só os rádios ligados.

Se tiver dois rádios do mesmo modelo, chamam-se por exemplo *IC-7300* e *IC-7300 2*.

## Desligar um rádio no The Rigger

O botão de ligar da ficha de um rádio desliga-o **só dentro do The Rigger**: a porta USB fica livre e as ligações desse rádio fecham-se. Serve quando outro programa tem de usar o rádio diretamente, por exemplo o programa do fabricante ou uma atualização de firmware.

O The Rigger lembra-se da escolha mesmo depois de reiniciar. Carregue de novo no botão para recuperar o rádio.

## Definições

### Geral

- **Idioma**: *Automático* usa o idioma do sistema; senão escolha italiano, inglês, francês, alemão, espanhol, português ou japonês. A janela inteira, o manual e as instruções dos programas mudam logo.
- **Arranque automático**: o The Rigger abre-se sozinho ao ligar o computador, assim os rádios estão prontos antes dos programas.

### Atualizações

- **Atualizações automáticas**: em cada arranque o The Rigger verifica se há uma versão nova. Se houver, descarrega-a, instala-a e reinicia sozinho em poucos segundos; os programas voltam a ligar-se sozinhos.
- **Procurar atualizações**: verifica já. A linha por baixo diz o que se passa (*já tem a versão mais recente*, *a transferir a atualização…*).

As pequenas correções da janela chegam num instante, mesmo sem reiniciar.

### Portas e drivers

- **Portas série por rádio** (Mac e Linux): quantas portas virtuais criar para cada rádio, de 1 a 16. Aplica-se logo; as portas em uso por um programa nunca são retiradas.
- **Drivers USB automáticos** (Windows): se ligar um rádio sem driver, o The Rigger instala o oficial (veja *Drivers USB*).

### Informações

Versão, créditos e o botão para oferecer um café ao IU1MVI com o PayPal.

## Drivers USB

- **Windows**: se ligar um rádio sem driver, o The Rigger descarrega o oficial assinado (do Windows Update ou do fabricante) e instala-o. O Windows pede confirmação uma só vez. Cobre Silicon Labs CP210x (Icom, Yaesu, Kenwood), FTDI (Elecraft e muitos cabos), WCH CH340 (Xiegu e cabos económicos) e Prolific.
- **macOS**: os drivers já estão no sistema, não é preciso nada.

## Rádios suportados

| Marca | Modelos |
|---|---|
| Icom | IC-7100, IC-7300, IC-7300MK2, IC-705, IC-7610, IC-7760, IC-9700, IC-905, IC-7851, IC-7800, IC-7700, IC-7600, IC-7410, IC-7200, IC-7000, IC-9100, IC-746PRO, IC-7400, IC-756 (todos), IC-718, IC-706 (todos), IC-703, IC-910H e os outros CI-V, recetores IC-R8600, IC-R75, IC-R30 |
| Xiegu | G90, X6100, X6200, X5105, X108G (protocolo Icom CI-V) |
| Kenwood | TS-890S, TS-990S, TS-590S/SG, TS-2000, TS-480, TS-870S, TS-570, TS-850, TS-450S, TS-690S e os outros com comandos CAT |
| Elecraft | K3, K3S, K4, KX2, KX3 |
| Yaesu | FTX-1, FTDX10, FTDX101D/MP, FT-710, FT-991/991A, FT-891, FTDX3000, FTDX5000, FTDX1200, FT-950, FT-2000, FT-450/450D, FTDX9000 |
| Yaesu clássicos | FT-817, FT-818, FT-857, FT-897 |
| FlexRadio | série 6000 através da porta CAT do SmartSDR |
| Compatíveis Kenwood | Lab599 TX-500, QRP Labs QDX/QMX, (tr)uSDX, Malachite e muitos SDR |

Os Icom com o endereço CI-V alterado no menu são encontrados na mesma.

## Problemas comuns

**O rádio não aparece.** Verifique se está ligado e com o cabo USB, depois carregue em *Procurar rádios de novo*. Se outro programa abriu a porta USB do rádio antes do The Rigger, feche-o: a porta tem de ficar com o The Rigger. Nos Icom, o *CI-V USB Baud Rate* deve estar em *Auto* ou num valor normal.

**No Windows o rádio não aparece e falta o driver.** Deixe ativo *Drivers USB automáticos* e confirme o pedido do Windows. Se não chegar, instale o driver do fabricante do cabo e carregue em *Procurar rádios de novo*.

**O programa não se liga.** Verifique neste manual a ligação escolhida e copie o endereço exato do separador Rádios (um clique copia-o). Depois carregue em *Testar ligação*: se todas as linhas tiverem ✓, o The Rigger funciona e o problema está nas definições do programa.

**A luz do programa está amarela.** O programa está ligado mas não pede nada ao rádio. Verifique no programa se o controlo CAT está ativo (costuma haver um botão *Connect* ou *Enable*).

**O PTT não funciona.** No programa o PTT tem de estar em **CAT** (ou *PTT via Radio Command*), não em RTS nem DTR.

**Um programa OmniRig diz que falta o OmniRig.** O The Rigger tem de ter sido aberto pelo menos uma vez neste computador. Abra-o e volte a abrir o programa.

**Uma porta já está a ser usada por outro programa.** Se o flrig, o rigctld ou outro programa ocupar as mesmas portas, o The Rigger usa a seguinte livre: copie o endereço exato do separador Rádios.

**Quero usar o rádio com o programa do fabricante.** Desligue o rádio no The Rigger com o seu botão de ligar: a porta USB fica livre.

---

The Rigger · software desenvolvido por IU1MVI · uso livre e gratuito para todos os radioamadores.
A compatibilidade OmniRig usa a interface pública do OmniRig de Alex Shovkoplyas, VE3NEA (licença MIT). Hamlib, flrig, TCI e Ham Radio Deluxe são marcas dos respetivos autores. 73!
