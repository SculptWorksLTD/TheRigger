# The Rigger — Manual

## O que faz

O The Rigger funciona como uma central entre os seus rádios e os programas do computador. Normalmente, a porta série de um rádio só pode ser usada por um programa de cada vez. O The Rigger é o único a falar com o rádio e dá a cada programa uma ligação só sua, para que o WSJT-X, o programa de registo, o de concursos e os outros trabalhem juntos no mesmo rádio sem se atrapalharem.

Gere vários rádios ao mesmo tempo, em Windows, macOS e Linux.

## Instalação

Transfira o ficheiro para o seu sistema na página **Releases** do projeto no GitHub.

- **Windows**: execute `therigger-windows-amd64.exe`. Se aparecer «O Windows protegeu o seu PC», escolha *Mais informações › Executar mesmo assim*.
- **macOS**: descompacte `TheRigger-macOS-arm64.zip` (Mac com chip Apple) ou `TheRigger-macOS-amd64.zip` (Mac Intel) e mova *The Rigger* para Aplicações. Da primeira vez: clique com o botão direito › *Abrir*.
- **Linux**: torne `therigger-linux-amd64` (ou `arm64`, por exemplo num Raspberry Pi) executável e execute-o.

A partir daí o The Rigger atualiza-se sozinho e arranca sozinho quando liga o computador.

## Primeiro arranque

Ao arrancar aparece a janela de boas-vindas com os créditos. Carregue em **Começar · 73**.

Ligue o rádio com o cabo USB e ligue-o. Em poucos segundos o The Rigger reconhece-o sozinho: experimenta as portas USB, o protocolo e a velocidade, e encontra o modelo. Não tem de configurar nada.

## A janela

A janela mostra apenas o necessário:

- **uma linha por rádio**, com uma luz: verde se o rádio está ligado e responde, cinzenta se está desligado ou sem cabo;
- **por baixo de cada rádio, os programas ligados**, cada um com a sua luz: verde se está a falar com o rádio, amarela se tem a porta aberta mas está parado.

Se por baixo de um rádio aparecer «nenhum programa ligado», nenhum programa o está a usar.

Em cima há três botões: **?** (como ligar os programas, e este manual), **⚙** (definições) e **⏻** (fecha o The Rigger).

Fechar a janela não desliga o The Rigger: fica na área de notificação, junto ao relógio, e os programas continuam ligados. Para a reabrir, clique no ícone e escolha *Mostrar janela*.

## Ligar os programas

Carregue em **?**: para cada programa o The Rigger diz exatamente o que configurar, com a porta já escolhida. O botão **Copiar** copia o nome da porta ou o endereço, para o colar no programa.

Há dois tipos de ligação:

1. **Hamlib NET rigctl**: para WSJT-X, JTDX, JS8Call, fldigi, CQRLOG e os outros programas que o suportam. No programa escolha *Hamlib NET rigctl* como rádio e o endereço indicado como servidor (por exemplo `127.0.0.1:4532`). Podem ligar-se todos os programas que quiser.
2. **Porta série**: para Log4OM, N1MM Logger+, HRD, Logger32, DXLab Commander, MixW e todos os outros. No programa escolha como rádio **o modelo real do seu rádio** (por exemplo Icom IC-7100) ou **Kenwood TS-2000**, e a porta indicada. Qualquer velocidade, sem controlo de fluxo, PTT por CAT.
   - No Windows são portas `COM` normais.
   - No Mac e no Linux estão em `/tmp/TheRigger/`, por exemplo `/tmp/TheRigger/IC-7100-1`.

**Reconhecimento automático**: cada porta reconhece sozinha o protocolo do programa (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 ou TS-2000). Se escolher o modelo real no programa, os comandos vão diretamente para o rádio e todas as suas funções ficam disponíveis. Se escolher Kenwood TS-2000 funcionam as funções comuns: frequência, modo, PTT e split. Com rádios Yaesu, da primeira vez que um programa configurado como TS-2000 usa uma porta, o PTT pode não atuar na primeira transmissão: a partir da segunda funciona, e a porta lembra-se.

Um programa por porta: o The Rigger já as atribui para que nunca entrem em conflito. Cada rádio tem 4 portas, que pode aumentar até 16 nas definições.

### Exemplos

- **WSJT-X**: *Definições › Rádio*: Rádio *Hamlib NET rigctl*, Servidor *127.0.0.1:4532*, PTT *CAT*.
- **Log4OM**: na configuração CAT escolha o rádio *Kenwood TS-2000* na porta indicada para o Log4OM. O OmniRig deixa de ser necessário.
- **N1MM Logger+**: *Config › Configure Ports*: Radio *Kenwood TS-2000*, a porta COM indicada para o N1MM, qualquer velocidade, *DTR* e *RTS* desligados.

## Definições

- **Idioma**: automático (o do sistema) ou um dos sete disponíveis.
- **Arranque automático**: o The Rigger arranca sozinho quando liga o computador.
- **Atualizações automáticas**: as versões novas instalam-se sozinhas, e só quando nenhum programa está a usar o rádio.
- **Drivers USB automáticos**: os drivers USB em falta instalam-se sozinhos.
- **Portas por rádio**: de 1 a 16. Aplica-se de imediato; as portas em uso nunca são retiradas.

## Drivers USB

- **Windows**: se ligar um rádio sem driver, o The Rigger transfere o driver oficial assinado do Windows Update (ou do fabricante) e instala-o. O Windows pede uma confirmação. Cobre Silicon Labs (Icom, Yaesu, Kenwood), FTDI (Elecraft e muitos cabos), WCH CH340 (Xiegu e cabos económicos) e Prolific.
- **Linux**: os drivers já estão no sistema. O The Rigger corrige sozinho as permissões das portas e o serviço *brltty*, que no Ubuntu bloqueia os cabos CH340. Pede a palavra-passe uma vez.
- **macOS**: os drivers já fazem parte do sistema.

As portas COM virtuais do Windows usam o driver gratuito *com0com*, que o The Rigger instala sozinho da primeira vez (com uma confirmação do Windows).

## Rádios suportados

- **Icom** e compatíveis CI-V (também Xiegu): IC-7100, IC-7300, IC-705, IC-7610, IC-9700, IC-905, IC-7760 e outros.
- **Kenwood**: TS-2000, TS-480, TS-590S/SG, TS-890S, TS-990S.
- **Elecraft**: K3, KX2, KX3, K4.
- **Yaesu** recentes: FT-991/A, FTDX10, FT-710, FTDX101, FT-891, FTDX3000 e outros.
- **Yaesu** clássicos: FT-817, FT-818, FT-857, FT-897.
- Outros rádios com comandos compatíveis Kenwood: Lab599 TX-500, QRP Labs QDX/QMX e muitos SDR.

## Problemas frequentes

- **O rádio não aparece**: verifique se está ligado e com o cabo USB. Nos Icom, a velocidade *CI-V USB* no menu do rádio deve estar em *Auto* ou num valor normal; *CI-V USB Echo Back* pode ficar como está.
- **Um programa não se liga**: carregue em **?** e verifique se escolheu *Kenwood TS-2000* (ou *Hamlib NET rigctl*) e a porta certa. Dois programas não podem usar a mesma porta série.
- **A luz de um programa está amarela**: o programa abriu a porta mas não interroga o rádio. Verifique se o CAT está ativo no programa.
- **O Windows não cria as portas COM**: em alguns PC com Windows 11 o driver *com0com* pode estar bloqueado. Nesse caso use a ligação *Hamlib NET rigctl*, que funciona sempre.

---

The Rigger · software desenvolvido por IU1MVI · uso livre e gratuito para todos os radioamadores. 73!
