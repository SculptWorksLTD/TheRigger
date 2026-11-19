# The Rigger — Manual

## Em resumo

O The Rigger é o único que fala com o rádio e dá a cada programa a sua própria ligação: WSJT-X, programas de log, de concurso e SDR trabalham juntos no mesmo rádio. Encontra os rádios sozinho, gere vários ao mesmo tempo e atualiza-se sozinho. Nunca transmite por iniciativa própria.

## Instalação

**Windows**: descarregue `The-Rigger-Windows.zip`, coloque **The Rigger.exe** numa pasta sua (por exemplo *Documentos*) e abra-o. Se aparecer *O Windows protegeu o seu PC*: **Mais informações › Executar mesmo assim**. Não é preciso instalar OmniRig, com0com nem Hamlib. O atalho no Ambiente de Trabalho cria-se sozinho.

**Mac**: descarregue `The-Rigger-Mac.pkg` (chip Apple) ou `The-Rigger-Mac-Intel.pkg` (Intel) e instale-o. Se o Mac não o abrir: *Definições do Sistema › Privacidade e segurança › Abrir mesmo assim*.

## Primeiro arranque

Ligue o rádio com o cabo USB e acenda-o: em poucos segundos aparece no separador **Rádios**. Não há nada para configurar no The Rigger. Depois configure os programas como abaixo.

## Ligar os programas

Três regras valem para todos os modos:

- **PTT** sempre em **CAT** (ou *PTT por comando do rádio*), nunca RTS ou DTR.
- Endereço sempre **127.0.0.1** (o seu computador).
- Depois de configurar, carregue em **Test**, **Connect** ou **OK** no programa.

Escolha o modo que o seu programa conhece:

| Modo | O que configura | Programas |
|---|---|---|
| Hamlib | *Hamlib NET rigctl* · `127.0.0.1:4532` | WSJT-X, JTDX, JS8Call, MacLoggerDX, Gpredict, CQRLOG, VarAC |
| flrig | *FLRig* · `127.0.0.1` porta `12345` | fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog, Cloudlog) |
| TCI | *TCI* · `127.0.0.1:40001` | N1MM Logger+, MSHV, Log4OM, DXLog |
| OmniRig (Windows) | *OmniRig* · *Rig 1* | Log4OM, HDSDR, SDR Console, CW Skimmer, MMSSTV, UcxLog |
| Ham Radio Deluxe | servidor `127.0.0.1` porta `7809` | HRD Logbook, DM-780 |
| DXLab Commander | `127.0.0.1` porta `52002` | BBLogger |
| CAT por rede | modelo real ou *Kenwood TS-2000* · `127.0.0.1:4600` | N1MM Logger+, DXLab Commander (modelo *Thetis*) |
| Portas série (Mac) | modelo real · porta `/tmp/TheRigger/…` · qualquer velocidade | RUMlogNG, SkookumLogger |

### Hamlib (WSJT-X e semelhantes)

1. **Rig**: *Hamlib NET rigctl* (em alguns programas *rigctld*, modelo 2).
2. **Servidor**: `127.0.0.1:4532`.
3. **PTT**: *CAT*. No WSJT-X carregue em **Test CAT**: fica verde.

### flrig

1. Escolha **FLRig** (no fldigi: *Rig Control › flrig › Connect to flrig*).
2. Endereço `127.0.0.1`, porta `12345`. Não é preciso instalar o flrig.

### TCI

1. Escolha **TCI**, endereço `127.0.0.1:40001`.
2. O áudio continua na placa de som do rádio, como sempre.

### OmniRig (só Windows)

1. Escolha **OmniRig** e depois **Rig 1** (segundo rádio **Rig 2**). Não instale o OmniRig verdadeiro.
2. Abra os programas normalmente, não *como administrador*.

### Ham Radio Deluxe

1. Servidor `127.0.0.1`, porta `7809`, carregue em **Connect**. Não é preciso abrir o HRD Rig Control.
2. MMTTY e MMVARI: copie o plugin gratuito **HRDPTT.mmr** para a pasta do programa e escolha **HRDPTT** como porta.

### DXLab Commander (BBLogger)

1. No BBLogger, *Preferences › CAT*: **IP** `127.0.0.1`, **Porta** `52002`, **Autostart** vazio. Sem CatBKT.
2. Na janela do QSO carregue em **CAT ON**.

### CAT por rede

1. Como rádio o **modelo real** (por exemplo *IC-7100*) ou **Kenwood TS-2000**, ligação **TCP**, `127.0.0.1` porta `4600`.
2. DXLab Commander: **Model** *Thetis*, **Communicate via TCP**, `127.0.0.1` porta `4600`.

### Portas série (Mac)

Como rádio o **modelo real** ou **Kenwood TS-2000**, porta `/tmp/TheRigger/IC-7100-1` (o nome segue o rádio), qualquer velocidade, sem handshake. Uma porta por programa.

### N3FJP (Windows)

*Rig Interface*: **None**. *Application Program Interface*: marque **TCP API Enabled**, porta `1100`. Banda, modo e frequência preenchem-se sozinhos.

### Segundo rádio

| Modo | Primeiro rádio | Segundo rádio |
|---|---|---|
| Hamlib | 4532 | 4534 |
| flrig | 12345 | 12346 |
| TCI | 40001 | 40002 |
| DXLab Commander | 52002 | 52102 |
| CAT por rede | 4600 | 4601 |
| OmniRig | Rig 1 | Rig 2 |
| Ham Radio Deluxe | rádio 1 | rádio 2 (mesma porta 7809) |

### Programas que não estão na lista

Procure no programa uma destas opções, por esta ordem: *Hamlib/rigctld*, *FLRig*, *TCI*, *OmniRig*, *Ham Radio Deluxe*, *TCP*. Use a linha correspondente da tabela. Os programas Windows que só conhecem portas COM (Logger32, Win-Test, SatPC32) não podem ser ligados: use Log4OM, N1MM ou Gpredict.

## A janela

- **Rádios**: os rádios encontrados, com frequência, modo e programas ligados. O botão de ligar do cartão liberta o rádio para outro programa (por exemplo o do fabricante); o rádio verdadeiro continua ligado.
- **Manual**: este manual.
- **Definições**: idioma, arranque automático, *Arrancar oculto*, atualizações, portas e drivers.

O The Rigger atualiza-se sozinho em cada arranque.

## Só Windows

- **Programas em conflito**: se o OmniRig verdadeiro, CatBKT, DXLab Commander, flrig, rigctld, HRD ou programas de portas COM virtuais ficarem com o rádio ou com as portas, aparece uma linha amarela no separador Rádios. **Ver** abre a lista com **Fechar…**, **Desinstalar…** ou **Limpar…** (restos do OmniRig no registo).
- **Limpeza do com0com**: *Definições › Portas e drivers › Limpar…* remove o com0com e as suas portas virtuais. Leia o aviso, confirme e reinicie no fim.
- **Drivers USB**: se faltar um, o The Rigger instala sozinho o oficial.

## Avisos e ideias

O botão com o balão, em cima à direita: **Algo não funciona** ou **Ideia ou pedido**. Anexe o registo do último arranque. É anónimo; o indicativo é facultativo. *Ver exatamente o que é enviado* mostra tudo antes do envio.

## Problemas comuns

- **O rádio não aparece**: acenda-o, verifique o cabo e carregue em *Procurar rádios de novo*. Feche os programas que abrem diretamente a porta USB do rádio.
- **O programa não liga**: verifique de novo modo e endereço na tabela. Se o programa estava aberto antes do The Rigger, carregue de novo em *Test* ou *Connect*.
- **O PTT não funciona**: no programa ponha o PTT em **CAT**.
- **OmniRig não encontrado**: abra o The Rigger pelo menos uma vez e volte a abrir o programa (não como administrador).

---

The Rigger · software de IU1MVI · gratuito para todos os radioamadores. A compatibilidade com o OmniRig usa a interface pública do OmniRig de VE3NEA (licença MIT). Hamlib, flrig, TCI e Ham Radio Deluxe são marcas dos respetivos autores. 73!
