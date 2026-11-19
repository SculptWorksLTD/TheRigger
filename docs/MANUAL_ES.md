# The Rigger — Manual

## En breve

The Rigger es el único que habla con la radio y da a cada programa su propia conexión: WSJT-X, libros de guardia, programas de concurso y SDR trabajan juntos con la misma radio. Encuentra las radios solo, maneja varias a la vez y se actualiza solo. Nunca transmite por su cuenta.

## Instalación

**Windows**: descarga `The-Rigger-Windows.zip`, pon **The Rigger.exe** en una carpeta tuya (por ejemplo *Documentos*) y ábrelo. Si aparece *Windows protegió su PC*: **Más información › Ejecutar de todas formas**. No hace falta instalar OmniRig, com0com ni Hamlib. El acceso directo en el Escritorio se crea solo.

**Mac**: descarga `The-Rigger-Mac.pkg` (chip Apple) o `The-Rigger-Mac-Intel.pkg` (Intel) e instálalo. Si el Mac no lo abre: *Ajustes del Sistema › Privacidad y seguridad › Abrir igualmente*.

## Primer inicio

Conecta la radio con el cable USB y enciéndela: en pocos segundos aparece en la pestaña **Radios**. No hay nada que configurar en The Rigger. Después configura los programas como se indica abajo.

## Conectar los programas

Tres reglas valen para todos los modos:

- **PTT** siempre en **CAT** (o *PTT por comando de radio*), nunca RTS o DTR.
- Dirección siempre **127.0.0.1** (tu ordenador).
- Después de configurar, pulsa **Test**, **Connect** u **OK** en el programa.

Elige el modo que conoce tu programa:

| Modo | Qué configuras | Programas |
|---|---|---|
| Hamlib | *Hamlib NET rigctl* · `127.0.0.1:4532` | WSJT-X, JTDX, JS8Call, MacLoggerDX, Gpredict, CQRLOG, VarAC |
| flrig | *FLRig* · `127.0.0.1` puerto `12345` | fldigi, QLog, Not1MM, HAMRS, WaveLogGate (Wavelog, Cloudlog) |
| TCI | *TCI* · `127.0.0.1:40001` | N1MM Logger+, MSHV, Log4OM, DXLog |
| OmniRig (Windows) | *OmniRig* · *Rig 1* | Log4OM, HDSDR, SDR Console, CW Skimmer, MMSSTV, UcxLog |
| Ham Radio Deluxe | servidor `127.0.0.1` puerto `7809` | HRD Logbook, DM-780 |
| DXLab Commander | `127.0.0.1` puerto `52002` | BBLogger |
| CAT por red | modelo real o *Kenwood TS-2000* · `127.0.0.1:4600` | N1MM Logger+, DXLab Commander (modelo *Thetis*) |
| Puertos serie (Mac) | modelo real · puerto `/tmp/TheRigger/…` · cualquier velocidad | RUMlogNG, SkookumLogger |

### Hamlib (WSJT-X y similares)

1. **Rig**: *Hamlib NET rigctl* (en algunos programas *rigctld*, modelo 2).
2. **Servidor**: `127.0.0.1:4532`.
3. **PTT**: *CAT*. En WSJT-X pulsa **Test CAT**: se pone verde.

### flrig

1. Elige **FLRig** (en fldigi: *Rig Control › flrig › Connect to flrig*).
2. Dirección `127.0.0.1`, puerto `12345`. No hace falta instalar flrig.

### TCI

1. Elige **TCI**, dirección `127.0.0.1:40001`.
2. El audio sigue en la tarjeta de sonido de la radio, como siempre.

### OmniRig (solo Windows)

1. Elige **OmniRig** y luego **Rig 1** (segunda radio **Rig 2**). No instales el OmniRig real.
2. Abre los programas normalmente, no *como administrador*.

### Ham Radio Deluxe

1. Servidor `127.0.0.1`, puerto `7809`, pulsa **Connect**. No hace falta abrir HRD Rig Control.
2. MMTTY y MMVARI: copia el plugin gratuito **HRDPTT.mmr** en la carpeta del programa y elige **HRDPTT** como puerto.

### DXLab Commander (BBLogger)

1. En BBLogger, *Preferences › CAT*: **IP** `127.0.0.1`, **Puerto** `52002`, **Autostart** vacío. Sin CatBKT.
2. En la ventana del QSO pulsa **CAT ON**.

### CAT por red

1. Como radio el **modelo real** (por ejemplo *IC-7100*) o **Kenwood TS-2000**, conexión **TCP**, `127.0.0.1` puerto `4600`.
2. DXLab Commander: **Model** *Thetis*, **Communicate via TCP**, `127.0.0.1` puerto `4600`.

### Puertos serie (Mac)

Como radio el **modelo real** o **Kenwood TS-2000**, puerto `/tmp/TheRigger/IC-7100-1` (el nombre sigue a la radio), cualquier velocidad, sin handshake. Un puerto por programa.

### N3FJP (Windows)

*Rig Interface*: **None**. *Application Program Interface*: marca **TCP API Enabled**, puerto `1100`. Banda, modo y frecuencia se rellenan solos.

### Segunda radio

| Modo | Primera radio | Segunda radio |
|---|---|---|
| Hamlib | 4532 | 4534 |
| flrig | 12345 | 12346 |
| TCI | 40001 | 40002 |
| DXLab Commander | 52002 | 52102 |
| CAT por red | 4600 | 4601 |
| OmniRig | Rig 1 | Rig 2 |
| Ham Radio Deluxe | radio 1 | radio 2 (mismo puerto 7809) |

### Programas que no están en la lista

Busca en el programa una de estas opciones, en este orden: *Hamlib/rigctld*, *FLRig*, *TCI*, *OmniRig*, *Ham Radio Deluxe*, *TCP*. Usa la fila correspondiente de la tabla. Los programas de Windows que solo conocen puertos COM (Logger32, Win-Test, SatPC32) no se pueden conectar: usa Log4OM, N1MM o Gpredict.

## La ventana

- **Radios**: las radios encontradas, con frecuencia, modo y programas conectados. El botón de encendido de la tarjeta libera la radio para otro programa (por ejemplo el del fabricante); la radio real sigue encendida.
- **Manual**: este manual.
- **Ajustes**: idioma, inicio automático, *Arrancar oculto*, actualizaciones, puertos y drivers.

The Rigger se actualiza solo en cada inicio.

## Solo Windows

- **Programas en conflicto**: si el OmniRig real, CatBKT, DXLab Commander, flrig, rigctld, HRD o programas de puertos COM virtuales se quedan con la radio o los puertos, aparece una línea amarilla en la pestaña Radios. **Ver** abre la lista con **Cerrar…**, **Desinstalar…** o **Limpiar…** (restos de OmniRig en el registro).
- **Limpieza de com0com**: *Ajustes › Puertos y drivers › Limpiar…* quita com0com y sus puertos virtuales. Lee el aviso, confirma y reinicia al final.
- **Drivers USB**: si falta uno, The Rigger instala solo el oficial.

## Avisos e ideas

El botón con el bocadillo, arriba a la derecha: **Algo no funciona** o **Idea o petición**. Adjunta el registro del último inicio. Es anónimo; el indicativo es opcional. *Ver exactamente lo que se envía* lo muestra todo antes de enviar.

## Problemas frecuentes

- **La radio no aparece**: enciéndela, revisa el cable y pulsa *Buscar radios de nuevo*. Cierra los programas que abren directamente el puerto USB de la radio.
- **El programa no se conecta**: revisa otra vez modo y dirección en la tabla. Si el programa estaba abierto antes que The Rigger, pulsa de nuevo *Test* o *Connect*.
- **El PTT no funciona**: en el programa pon el PTT en **CAT**.
- **No se encuentra OmniRig**: abre The Rigger al menos una vez y vuelve a abrir el programa (no como administrador).

---

The Rigger · software de IU1MVI · gratis para todos los radioaficionados. La compatibilidad con OmniRig usa la interfaz pública de OmniRig de VE3NEA (licencia MIT). Hamlib, flrig, TCI y Ham Radio Deluxe son marcas de sus respectivos autores. ¡73!
