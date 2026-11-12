# The Rigger — Manual

## Qué hace

The Rigger hace de centralita entre tus radios y los programas del ordenador.

Normalmente el puerto CAT de una radio solo lo puede usar un programa a la vez: si WSJT-X lo abre, el libro de guardia ya no lo encuentra. Con The Rigger es distinto. The Rigger es el único que habla con la radio y da a cada programa una conexión propia. Así WSJT-X, el libro de guardia, el programa de concursos, CWIU1MVI, el programa SDR y los demás trabajan juntos en la misma radio sin molestarse.

En resumen:

- **encuentra las radios solo**: conectas el cable USB y la radio aparece, sin elegir puerto, velocidad ni modelo;
- **varias radios a la vez**: cada una tiene sus conexiones;
- **todas las conexiones que usan los programas**: Hamlib, flrig, TCI, OmniRig (Windows), Ham Radio Deluxe, CAT por red y puertos serie (Mac y Linux);
- **se actualiza solo** y habla 10 idiomas.

The Rigger nunca transmite por su cuenta ni cambia nada en la radio: solo hace lo que piden los programas.

## Instalación

Descarga el archivo de tu sistema desde la página **Releases** del proyecto en GitHub (SculptWorksLTD/TheRigger).

### Windows

1. Descarga `The-Rigger-…-Windows.zip`.
2. Abre el zip y arrastra **The Rigger.exe** a una carpeta tuya, por ejemplo *Documentos › The Rigger*. No lo dejes dentro del zip ni en una carpeta de descargas temporal.
3. Haz doble clic en **The Rigger.exe**.
4. Si aparece *Windows protegió su PC*, pulsa **Más información** y luego **Ejecutar de todas formas**. Solo pasa la primera vez.

No hay que instalar nada más: ni OmniRig, ni com0com, ni Hamlib.

### macOS

1. Descarga `The-Rigger-…-Mac.pkg` si tu Mac tiene chip Apple (M1, M2, M3, M4), o `The-Rigger-…-Mac-Intel.pkg` para un Mac Intel.
2. Abre el archivo y sigue la instalación: The Rigger queda en **Aplicaciones**.
3. Si el Mac no lo abre: clic derecho en el archivo › **Abrir**, o *Ajustes del Sistema › Privacidad y seguridad › Abrir igualmente*.

Desde entonces The Rigger se actualiza solo.

## Primer inicio

Al iniciar aparece la ventana de bienvenida con los créditos: pulsa **Empezar · 73**.

Conecta la radio con el cable USB y enciéndela. En pocos segundos The Rigger la encuentra: prueba los puertos USB, el protocolo (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817) y la velocidad, y reconoce el modelo. No tienes que configurar nada.

Cuando la radio aparezca en la pestaña **Radios** estará lista: para configurar cada programa mira el capítulo **Instrucciones para los programas** de este manual.

## La ventana

La ventana tiene tres pestañas, arriba en el centro:

- **Radios**: las radios encontradas, con frecuencia, modo y programas conectados;
- **Manual**: este manual, con el índice a la izquierda;
- **Ajustes**: idioma, inicio, actualizaciones, puertos e información.

Arriba a la derecha hay dos botones:

- **Ocultar** (flecha hacia abajo): oculta la ventana. En Mac The Rigger queda en la barra de menús, junto al reloj: haz clic en el icono y elige *Mostrar The Rigger*. En Windows la ventana va a la barra de tareas.
- **Apagar** (⏻): cierra The Rigger. Los programas conectados pierden la radio hasta que lo vuelvas a abrir.

Abajo está la barra de estado: la luz es verde cuando hay al menos una radio conectada y amarilla cuando hay un aviso. El botón con la flecha circular busca las radios de nuevo. La versión está a la derecha.

Puedes cambiar el tamaño de la ventana arrastrando sus bordes.

## Pestaña Radios

Cada radio encontrada tiene su propia ficha.

### Cabecera

- **Botón de encendido** (a la izquierda): activa o apaga la radio *dentro de The Rigger*. Apagada, The Rigger cierra su puerto USB y lo deja libre, por ejemplo para el programa del fabricante o una actualización de firmware. Pulsa otra vez para recuperarla. La radio real no se apaga.
- **Nombre**: el modelo, con un número si tienes dos radios iguales (por ejemplo *IC-7300 2*).
- **Estado**: *conectada* (responde), *desconectada* (cable quitado o radio apagada) o *apagada* (apagada en The Rigger).

### Pantalla

- **Frecuencia** del VFO en uso, en grande, con el **modo** al lado (USB, LSB, CW, CW-R, RTTY, AM, FM, USB-D, LSB-D, FM-D).
- **A** y **B**: qué VFO está en uso.
- **SPLIT**: encendido cuando la radio está en split.
- **TX**: se pone rojo cuando la radio transmite.
- Debajo: la frecuencia del otro VFO y la barra del **S-meter**.

La pantalla sigue a la radio en tiempo real, tanto al girar el mando como cuando un programa cambia la frecuencia.

### Datos de la radio

La línea gris muestra modelo, puerto USB, velocidad y, si la radio está activa en The Rigger, su número (**Rig 1**, **Rig 2**…). Ese número lo usan OmniRig y Ham Radio Deluxe.

### Programas conectados

La lista de programas que usan esta radio, cada uno con una luz:

- **verde**: el programa está hablando con la radio;
- **amarilla**: el programa está conectado pero ahora no pide nada.

A la derecha está la conexión que usa (por ejemplo `tcp:4532`, `flrig`, `TCI`, un puerto serie). Haz clic para copiar su dirección.

### Botones

- **Probar conexión**: se hace pasar por un programa y lee la frecuencia por cada conexión (puerto serie, Hamlib, flrig, CAT por red, TCI). Cada línea con **✓** funciona, cada línea con **✗** tiene un problema. La prueba solo lee: nunca transmite ni cambia nada.

### Buscar radios de nuevo

El botón **Buscar radios de nuevo** (arriba a la derecha de la pestaña, o la flecha circular de abajo) vuelve a revisar todos los puertos USB enseguida. Úsalo después de encender una radio que The Rigger no veía, o después de cerrar un programa que tenía ocupado el puerto.

## Las conexiones

The Rigger abre todas estas conexiones para cada radio a la vez. Cada programa usa la que conoce, y varios programas pueden compartir la misma conexión.

| Conexión | Dirección (primera radio) | Segunda radio | Sistemas |
|---|---|---|---|
| Hamlib NET rigctl | 127.0.0.1:4532 | 127.0.0.1:4534 | todos |
| flrig | 127.0.0.1:12345 | 127.0.0.1:12346 | todos |
| TCI | 127.0.0.1:40001 | 127.0.0.1:40002 | todos |
| DXLab Commander | 127.0.0.1:52002 | 127.0.0.1:52102 | todos |
| CAT por red (Kenwood TS-2000) | 127.0.0.1:4600 | 127.0.0.1:4601 | todos |
| Ham Radio Deluxe | 127.0.0.1:7809 (radio 1) | mismo puerto, radio 2 | todos |
| OmniRig | Rig 1 | Rig 2 | Windows |
| Puertos serie | /tmp/TheRigger/… | /tmp/TheRigger/… | Mac y Linux |

Si un puerto ya lo ocupa otro programa (por ejemplo un flrig o rigctld reales ya abiertos), The Rigger usa el siguiente libre: ves la dirección exacta pulsando *Probar conexión* en la ficha de la radio.

### Hamlib NET rigctl

Es la conexión de WSJT-X, JTDX, JS8Call, FreeDV, Gpredict, CQRLOG, KLog, MacLoggerDX, Pat y de todos los programas que usan Hamlib.

En el programa elige como radio **Hamlib NET rigctl** (en algunos programas *NET rigctl* o *rigctld*, modelo Hamlib número 2) y como servidor la dirección indicada, por ejemplo `127.0.0.1:4532`. PTT en **CAT**.

### flrig

The Rigger responde exactamente como flrig (W1HKJ). Es la conexión de fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog y Cloudlog), WFDlogger y de todos los programas con la opción *FLRig*.

En el programa elige **FLRig**, dirección `127.0.0.1` y puerto `12345` (segunda radio `12346`). No hace falta instalar flrig.

### TCI

The Rigger responde como un equipo TCI (el protocolo de Expert Electronics). Lo usan N1MM Logger+, JTDX, MSHV, Log4OM, QLog, Swisslog, DXLog y otros.

En el programa elige **TCI** y la dirección `127.0.0.1:40001` (segunda radio `40002`). El TCI de The Rigger transporta frecuencias, modo, PTT y split; el audio sigue en la tarjeta de sonido de la radio como siempre.

### DXLab Commander (para BBLogger)

The Rigger también responde como DXLab Commander, con los mismos mensajes de red. Lo usa BBLogger y, si quieres, WSJT-X, JTDX y MSHV con la radio *DX Lab Suite Commander*.

Dirección `127.0.0.1:52002` (segunda radio `52102`). Frecuencia, modo, PTT y split. Si en el PC ya funciona el DXLab Commander de verdad, el puerto 52002 sigue siendo suyo y The Rigger no lo usa.

### OmniRig (solo Windows)

The Rigger ocupa el lugar de OmniRig: **no hace falta instalar OmniRig**. En el programa elige **OmniRig** y luego **Rig 1** para la primera radio activa en The Rigger o **Rig 2** para la segunda.

Funciona con Log4OM, DXLog.net, HDSDR, SDR Console, CW Skimmer, UcxLog, Swisslog, MixW, QARTest, VarAC y con todos los programas que usan OmniRig, tanto de 32 como de 64 bits. Si un programa pide OmniRig con The Rigger cerrado, Windows abre The Rigger solo, oculto.

Si también tienes instalado el OmniRig real, los programas encuentran igualmente The Rigger, salvo los que se inician *como administrador*: inícialos normalmente. No dejes abiertos los dos a la vez sobre la misma radio.

### Ham Radio Deluxe

The Rigger responde como *HRD Rig Control*. Sirve para HRD Logbook, DM-780 y los programas que se conectan a Ham Radio Deluxe (también WSJT-X y JTDX con la opción *Ham Radio Deluxe*).

En el programa configura el servidor `127.0.0.1` puerto `7809`. Las radios se llaman igual que en The Rigger y están numeradas 1, 2, 3… en el orden de la pestaña Radios.

### CAT por red (TCP)

Una dirección que se comporta como el puerto serie de la radio. Sirve para los programas que saben conectarse a una radio por TCP, como N1MM Logger+ y MSHV.

En el programa elige como radio **el modelo real** (por ejemplo *IC-7100*) o **Kenwood TS-2000**, y como puerto la dirección indicada, por ejemplo `127.0.0.1:4600`. PTT en **CAT**.

### Puertos serie (Mac y Linux)

Para los programas que exigen un puerto serie, The Rigger crea algunos puertos virtuales para cada radio, por ejemplo `/tmp/TheRigger/IC-7100-1`, `/tmp/TheRigger/IC-7100-2`…

En el programa elige el **modelo real** o **Kenwood TS-2000**, el puerto indicado, velocidad **cualquiera**, control de flujo **ninguno**, PTT **CAT**.

Cada puerto reconoce solo el lenguaje del programa: Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 o TS-2000. Con el modelo real llegan a la radio todos los comandos, también los especiales. Con TS-2000 funcionan frecuencia, modo, PTT y split.

Un programa por puerto: The Rigger da a cada programa un puerto distinto. El número de puertos por radio se cambia en Ajustes (de 1 a 16).

En Windows The Rigger no crea puertos COM virtuales: usa las otras conexiones, que no necesitan drivers.

### CWIU1MVI

CWIU1MVI encuentra The Rigger solo: en la lista de radios de CWIU1MVI elige **The Rigger · nombre de la radio**. No hay nada más que configurar.

## Instrucciones para los programas

Estos son los pasos para los programas más usados. Las direcciones son las de la primera radio: para las demás, mira la tabla del capítulo *Las conexiones*.

### WSJT-X, JTDX, JS8Call, WSJT-Z

1. *File › Settings › Radio*.
2. **Rig**: *Hamlib NET rigctl*.
3. **Network Server**: `127.0.0.1:4532`.
4. **PTT Method**: *CAT*.
5. **Mode**: *Data/Pkt* si quieres la radio en USB-D, si no *USB*.
6. **Split Operation**: *Rig* o *Fake It*, como prefieras.
7. Pulsa **Test CAT**: se pone verde. Luego **OK**.

### fldigi

1. *Configure › Config dialog › Rig Control › flrig*.
2. Marca **Connect to flrig**, dirección `127.0.0.1`, puerto `12345`.
3. Desmarca *Hamlib* y *RigCAT* si están marcados.
4. **Save** y cierra: la frecuencia de fldigi sigue a la radio.

### Log4OM 2 (Windows)

1. *Settings › CAT interface*.
2. **CAT engine**: *OmniRig*. **Rig**: *Rig 1* (o *Rig 2* para la segunda radio).
3. Marca **Autostart** y pulsa **Connect**.

No hace falta instalar OmniRig. Como alternativa elige *Hamlib* › *Connect to active HAMLIB interface* con el puerto `4532`.

### N1MM Logger+ (Windows)

1. *Config › Configure Ports, Mode Control, Winkey, etc… › Hardware*.
2. En una línea de puerto elige **TCP**, **Radio**: *IC-7100* (el modelo real) o *Kenwood TS-2000*.
3. Pulsa **Set** y escribe la dirección `127.0.0.1` puerto `4600`.
4. Activa **PTT via Radio Command**.
5. **OK**: abajo a la izquierda aparece la frecuencia.

Como alternativa N1MM puede usar **TCI** con `127.0.0.1:40001`.

### HRD Logbook y DM-780 (Windows)

En la ventana de conexión con la radio elige el servidor `127.0.0.1` puerto `7809` y pulsa **Connect**. No hace falta abrir *HRD Rig Control*: responde The Rigger.

### QLog

1. *Settings › Equipment › Rig*, añade una radio.
2. **Interface**: *FLRig*, host `127.0.0.1`, puerto `12345` (o *Hamlib* › *NET rigctl* con `127.0.0.1:4532`).
3. Guarda y conecta la radio desde el menú *Equipment*.

### MacLoggerDX (Mac)

1. *Prefs › Radio*.
2. Elige **Hamlib rigctld**, host `127.0.0.1`, puerto `4532`.
3. Activa **Radio VFO** en la ventana de control.

Como alternativa elige el modelo real de la radio y un puerto de `/tmp/TheRigger/`.

### RUMlogNG y SkookumLogger (Mac)

En las preferencias de la radio elige el **modelo real** (o Kenwood TS-2000) y un puerto de `/tmp/TheRigger/`, por ejemplo `/tmp/TheRigger/IC-7100-2`, velocidad cualquiera.

### Wavelog y Cloudlog (con WaveLogGate)

En WaveLogGate abre *Config › Radio*, elige **FLRig**, host `127.0.0.1`, puerto `12345`, y guarda. Wavelog recibe frecuencia y modo y puede cambiarlos.

### HAMRS, Not1MM, WFDlogger

En los ajustes de control de la radio elige **FLRig**, host `127.0.0.1`, puerto `12345`.

### MSHV

*Options › Radio and Network Configuration*: elige **TCI** y la dirección `127.0.0.1:40001`.

### HDSDR, SDR Console, CW Skimmer (Windows)

Elige **OmniRig** (en HDSDR *Options › CAT to Radio (Omni-Rig)*, en SDR Console *Radio › External Radio*, en CW Skimmer *Setup › Radio*) y luego **Rig 1**.

### Gpredict

*Edit › Preferences › Interfaces › Radios › Add new*: host `localhost`, puerto `4532`, tipo *RX + TX* o el que necesites.

### CQRLOG (Linux)

*Preferences › TRX control*: desmarca *Run rigctld*, **Rig model**: *2 Hamlib NET rigctl*, **Device**: `127.0.0.1:4532`.

### VarAC (Windows)

*Settings › Rig control*: elige **OmniRig** y *Rig 1*, o **Hamlib (rigctld)** con `127.0.0.1` puerto `4532`.

### DXLab Commander (Windows)

Commander no sabe usar OmniRig ni Hamlib, pero sí hablar por red con Thetis: The Rigger responde como Thetis.

1. *Config › Ports*, panel de la radio: **Model**: *Thetis*.
2. Marca **Communicate via TCP**, **IP Address** `127.0.0.1`, **IP Port** `4600` (segunda radio `4601`).
3. Cierra la configuración: Commander muestra la frecuencia, y con él DXKeeper, SpotCollector y el resto de la suite DXLab.

### N3FJP ACLog y programas de concursos N3FJP (Windows)

Los programas N3FJP no saben compartir una radio sin puerto COM, pero tienen una interfaz de red: The Rigger la usa solo para enviar banda, modo y frecuencia de la primera radio activa.

1. *Settings › Rig Interface*: elige **None**.
2. *Settings › Application Program Interface*: marca **TCP API Enabled (Server)**, puerto `1100`.
3. Listo: banda, modo y frecuencia se rellenan solos. The Rigger nunca registra QSO por ti.

Así ACLog no puede cambiar la frecuencia de la radio (por ejemplo al hacer clic en un spot).

### BBLogger (Windows)

BBLogger no habla con la radio por sí solo: usa un programa CAT externo con los mensajes de DXLab Commander. The Rigger ocupa su lugar, sin CatBKT.

1. En BBLogger abre *Strumenti › Configurazione/Manutenzione › Preferences* (o *Configurar el CAT*).
2. En el recuadro **CAT** deja **IP** `127.0.0.1` y **Porta** `52002` (segunda radio `52102`). No hace falta pulsar *Download* ni instalar CatBKT.
3. Deja vacío **Autostart**: The Rigger ya está abierto.
4. Cierra la ventana: BBLogger muestra frecuencia y modo de la radio, y puedes cambiarlos desde la ventana del QSO.

Si BBLogger no lee la frecuencia, cierra CatBKT o DXLab Commander si están abiertos: ocupan el puerto 52002.

### MMSSTV, MMTTY y MMVARI (Windows)

- **MMSSTV**: *Option › Setup › TX › Radio command*, elige **OmniRig** y *Rig 1*.
- **MMTTY y MMVARI**: descarga el plugin gratuito **HRDPTT.mmr** (hace que los programas MM hablen con Ham Radio Deluxe), cópialo en la carpeta del programa, luego *Option › Setup › TX › Radio command* y elige **HRDPTT** como puerto. The Rigger responde como Ham Radio Deluxe, así que el PTT pasa por The Rigger.

### Programas que solo quieren un puerto COM (Windows)

Logger32, Win-Test, Winlink Express y SatPC32 solo conocen los puertos COM, que en Windows necesitan un driver firmado por Microsoft: por ahora The Rigger no se puede usar con estos programas. Esto es lo que puedes usar en su lugar, todo gratuito o ya compatible con The Rigger:

| En lugar de | Usa | Conexión |
|---|---|---|
| Logger32 | Log4OM 2, Swisslog, UcxLog, QLog o la suite DXLab | OmniRig, Hamlib, flrig o Thetis (Commander) |
| Win-Test | N1MM Logger+, DXLog.net o QARTest | CAT por red / TCI, OmniRig |
| Winlink Express | Pat Winlink, o Winlink Express sin control de la radio (frecuencia a mano) | Hamlib |
| SatPC32 | Gpredict | Hamlib |

### Programas que no están en la lista

Mira qué conexión conoce el programa:

- si tiene *Hamlib*, *NET rigctl* o *rigctld*, usa Hamlib (`127.0.0.1:4532`);
- si tiene *FLRig*, usa flrig (`127.0.0.1:12345`);
- si tiene *TCI*, usa TCI (`127.0.0.1:40001`);
- si tiene *OmniRig* (Windows), usa OmniRig *Rig 1*;
- si tiene *Ham Radio Deluxe*, usa `127.0.0.1:7809`;
- si se conecta a una radio por TCP, usa el CAT por red (`127.0.0.1:4600`) con el modelo real o Kenwood TS-2000;
- si solo quiere un puerto serie (Mac y Linux), usa un puerto de `/tmp/TheRigger/`.

## Varias radios a la vez

The Rigger gestiona todas las radios que conectes. Cada radio tiene:

- sus propias direcciones (puertos distintos, mira la tabla del capítulo *Las conexiones*);
- su número (**Rig 1**, **Rig 2**…) para OmniRig y Ham Radio Deluxe, según el orden de la pestaña Radios contando solo las radios activas.

Si tienes dos radios del mismo modelo se llaman, por ejemplo, *IC-7300* e *IC-7300 2*.

## Apagar una radio en The Rigger

El botón de encendido de la ficha de una radio la apaga **solo dentro de The Rigger**: el puerto USB queda libre y las conexiones de esa radio se cierran. Sirve cuando otro programa tiene que usar la radio directamente, por ejemplo el programa del fabricante o una actualización de firmware.

The Rigger recuerda la elección también tras reiniciar. Pulsa el botón otra vez para recuperar la radio.

## Ajustes

### General

- **Idioma**: *Automático* usa el idioma del sistema; si no, elige entre italiano, inglés, francés, alemán, español, portugués, japonés, ruso, árabe y chino. Cambian enseguida toda la ventana, el manual y las instrucciones de los programas.
- **Inicio automático**: The Rigger se abre solo al encender el ordenador, así las radios están listas antes que los programas.

### Actualizaciones

- **Actualizaciones automáticas**: en cada inicio The Rigger comprueba si hay una versión nueva. Si la hay, la descarga, la instala y se reinicia solo en pocos segundos; los programas se reconectan solos.
- **Buscar actualizaciones**: comprueba ahora mismo. La línea de abajo dice qué pasa (*ya tienes la última versión*, *descargando la actualización…*).

Las pequeñas correcciones de la ventana llegan al instante, incluso sin reiniciar.

### Puertos y drivers

- **Puertos serie por radio** (Mac y Linux): cuántos puertos virtuales crear para cada radio, de 1 a 16. Se aplica enseguida; los puertos que usa un programa nunca se quitan.
- **Drivers USB automáticos** (Windows): si conectas una radio sin driver, The Rigger instala el oficial (mira *Drivers USB*).

### Información

Versión, créditos y el botón para invitar a un café a IU1MVI con PayPal.

## Drivers USB

- **Windows**: si conectas una radio sin driver, The Rigger descarga el oficial firmado (de Windows Update o del fabricante) y lo instala. Windows pide confirmación una sola vez. Cubre Silicon Labs CP210x (Icom, Yaesu, Kenwood), FTDI (Elecraft y muchos cables), WCH CH340 (Xiegu y cables económicos) y Prolific.
- **macOS**: los drivers ya están en el sistema, no hace falta nada.

## Radios compatibles

| Marca | Modelos |
|---|---|
| Icom | IC-7100, IC-7300, IC-7300MK2, IC-705, IC-7610, IC-7760, IC-9700, IC-905, IC-7851, IC-7800, IC-7700, IC-7600, IC-7410, IC-7200, IC-7000, IC-9100, IC-746PRO, IC-7400, IC-756 (todas), IC-718, IC-706 (todas), IC-703, IC-910H y las demás CI-V, receptores IC-R8600, IC-R75, IC-R30 |
| Xiegu | G90, X6100, X6200, X5105, X108G (protocolo Icom CI-V) |
| Kenwood | TS-890S, TS-990S, TS-590S/SG, TS-2000, TS-480, TS-870S, TS-570, TS-850, TS-450S, TS-690S y las demás con comandos CAT |
| Elecraft | K3, K3S, K4, KX2, KX3 |
| Yaesu | FTX-1, FTDX10, FTDX101D/MP, FT-710, FT-991/991A, FT-891, FTDX3000, FTDX5000, FTDX1200, FT-950, FT-2000, FT-450/450D, FTDX9000 |
| Yaesu clásicas | FT-817, FT-818, FT-857, FT-897 |
| FlexRadio | serie 6000 a través del puerto CAT de SmartSDR |
| Compatibles Kenwood | Lab599 TX-500, QRP Labs QDX/QMX, (tr)uSDX, Malachite y muchas SDR |

Las Icom con la dirección CI-V cambiada en el menú se encuentran igualmente.

## Limpieza de com0com (Windows)

### Qué hace

Muestra cada paso en la ventana de The Rigger. Busca com0com, el driver gratuito que crea pares de puertos COM virtuales, y después: lo desinstala, quita todos sus puertos virtuales (también los “fantasma” que el Administrador de dispositivos no muestra), quita su driver de Windows y libera los números COM que esos puertos tenían ocupados. Antes de tocar nada te muestra lo que ha encontrado y pide confirmación; al final propone reiniciar.

### Por qué usarla

Con el tiempo com0com deja decenas o cientos de puertos virtuales y números COM reservados: los nuevos puertos USB reciben números altísimos, Windows muestra errores sin parar, los programas de radio se confunden y el PC va más lento. The Rigger no usa puertos COM virtuales (los programas se conectan con OmniRig, Hamlib, flrig, TCI, HRD o CAT por red: mira el Manual), así que com0com ya no hace falta.

### Riesgos

Hace falta permiso de administrador. Los programas que usan com0com dejan de funcionar con esos puertos: por ejemplo un divisor de puertos o dos programas unidos con puertos virtuales. Los puertos COM reales (radios, cables USB-serie) no se tocan. No se puede deshacer: si vuelves a necesitar com0com tendrás que reinstalarlo. Cierra antes los programas que usan puertos COM. La usas bajo tu responsabilidad: el autor no responde de posibles problemas.

### Cómo se usa

**Ajustes → Puertos y drivers → Limpieza de com0com → Limpiar…** (el botón solo está activo si com0com está en el PC). Lee el aviso, marca *Lo he leído y lo entiendo* y pulsa **Iniciar la limpieza**. Windows pide permiso de administrador: responde **Sí**. Los pasos aparecen en la misma ventana de The Rigger; tras la búsqueda pulsa **Seguir** (o **Cancelar** para no tocar nada). Al final puedes pulsar **Reiniciar ahora** o **Cerrar**. Si la ventana dice que quedan dispositivos, reinicia el PC y repite la limpieza.

## Avisos e ideas

El botón con el bocadillo, arriba a la derecha, sirve para avisar de un problema o proponer una idea, gratis y de forma anónima.

- **Algo no funciona**: escribe qué hacías, qué esperabas y qué pasó; indica radio y programa. Normalmente conviene adjuntar el registro del **último arranque**; si el problema ocurre de vez en cuando, el de los **últimos 7 días**.
- **Idea o petición**: una función nueva, un programa que conectar, una radio que añadir. Se valoran todas las ideas; las útiles para muchos entran en las siguientes versiones.

**Anonimato.** No enviamos nombre, indicativo, email ni dirección IP. Antes de enviar, The Rigger quita del registro usuario, nombre del PC, carpetas personales y direcciones de red. Con *Ver exactamente lo que se envía* compruebas palabra por palabra lo que sale. No escribas datos personales en el texto.

El registro es un archivo de texto que The Rigger guarda en tu ordenador (los últimos 12 arranques); solo se envía si tú lo eliges.

## Problemas frecuentes

**La radio no aparece.** Comprueba que esté encendida y conectada con el cable USB, y pulsa *Buscar radios de nuevo*. Si otro programa abrió el puerto USB de la radio antes que The Rigger, ciérralo: el puerto lo tiene que tener The Rigger. En las Icom, el *CI-V USB Baud Rate* debe estar en *Auto* o en un valor normal.

**En Windows la radio no aparece y falta el driver.** Deja activado *Drivers USB automáticos* y confirma la petición de Windows. Si no basta, instala el driver del fabricante del cable y pulsa *Buscar radios de nuevo*.

**El programa no se conecta.** Comprueba en este manual la conexión elegida y la dirección. Luego pulsa *Probar conexión* en la ficha de la radio: muestra las direcciones exactas y, si todas las líneas tienen ✓, The Rigger funciona y el problema está en los ajustes del programa.

**La luz del programa es amarilla.** El programa está conectado pero no pide nada a la radio. Comprueba en el programa que el control CAT esté activado (suele haber un botón *Connect* o *Enable*).

**El PTT no funciona.** En el programa el PTT debe estar en **CAT** (o *PTT via Radio Command*), no en RTS ni DTR.

**Un programa OmniRig dice que falta OmniRig.** The Rigger debe haberse abierto al menos una vez en este ordenador. Ábrelo y vuelve a abrir el programa.

**Un puerto ya lo usa otro programa.** Si flrig, rigctld u otro programa ocupa los mismos puertos, The Rigger toma el siguiente libre: comprueba la dirección exacta con *Probar conexión*.

**Quiero usar la radio con el programa del fabricante.** Apaga la radio en The Rigger con su botón de encendido: el puerto USB queda libre.

---

The Rigger · software desarrollado por IU1MVI · uso libre y gratuito para todos los radioaficionados.
La compatibilidad OmniRig usa la interfaz pública de OmniRig de Alex Shovkoplyas, VE3NEA (licencia MIT). Hamlib, flrig, TCI y Ham Radio Deluxe son marcas de sus respectivos autores. ¡73!
