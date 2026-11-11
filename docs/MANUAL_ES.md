# The Rigger — Manual

## Qué hace

The Rigger hace de centralita entre tus radios y los programas del ordenador. Normalmente, el puerto serie de una radio solo lo puede usar un programa a la vez. The Rigger es el único que habla con la radio y da a cada programa una conexión propia, así WSJT-X, el programa de registro, el de concursos y los demás trabajan juntos con la misma radio sin estorbarse.

Gestiona varias radios a la vez, en Windows y macOS.

## Instalación

Descarga el archivo para tu sistema desde la página **Releases** del proyecto en GitHub.

- **Windows**: ejecuta `therigger-windows-amd64.exe`. Si aparece «Windows protegió su PC», elige *Más información › Ejecutar de todas formas*.
- **macOS**: descomprime `TheRigger-macOS-arm64.zip` (Mac con chip Apple) o `TheRigger-macOS-amd64.zip` (Mac Intel) y mueve *The Rigger* a Aplicaciones. La primera vez: clic derecho › *Abrir*.

A partir de ahí The Rigger se actualiza solo y arranca solo al encender el ordenador.

## Primer arranque

Al arrancar aparece la ventana de bienvenida con los créditos. Pulsa **Empezar · 73**.

Conecta la radio con el cable USB y enciéndela. En pocos segundos The Rigger la reconoce solo: prueba los puertos USB, el protocolo y la velocidad, y encuentra el modelo. No tienes que configurar nada.

## La ventana

La ventana muestra solo lo necesario:

- **una línea por radio**, con una luz: verde si la radio está conectada y responde, gris si está apagada o desconectada;
- **debajo de cada radio, los programas conectados**, cada uno con su luz: verde si está hablando con la radio, amarilla si tiene el puerto abierto pero está parado.

Si debajo de una radio pone «ningún programa conectado», ningún programa la está usando.

Arriba hay tres botones: **?** (cómo conectar los programas, y este manual), **⚙** (ajustes) y **⏻** (cierra The Rigger).

Cerrar la ventana no apaga The Rigger: sigue en el área de notificación, junto al reloj, y los programas siguen conectados. Para volver a abrirla, haz clic en el icono y elige *Mostrar ventana*.

## Conectar los programas

Pulsa **?**: para cada programa The Rigger te dice exactamente qué configurar, con el puerto ya elegido. El botón **Copiar** copia el nombre del puerto o la dirección para pegarlo en el programa.

Hay dos tipos de conexión:

1. **Hamlib NET rigctl**: para WSJT-X, JTDX, JS8Call, fldigi, CQRLOG y los demás programas que lo admiten. En el programa elige *Hamlib NET rigctl* como radio y la dirección indicada como servidor (por ejemplo `127.0.0.1:4532`). Se pueden conectar todos los programas que quieras.
2. **Puerto serie**: para Log4OM, N1MM Logger+, HRD, Logger32, DXLab Commander, MixW y todos los demás. En el programa elige como radio **el modelo real de tu radio** (por ejemplo Icom IC-7100) o **Kenwood TS-2000**, y el puerto indicado. Velocidad cualquiera, sin control de flujo, PTT por CAT.
   - En Windows son puertos `COM` normales.
   - En Mac están en `/tmp/TheRigger/`, por ejemplo `/tmp/TheRigger/IC-7100-1`.

**Reconocimiento automático**: cada puerto reconoce solo el protocolo del programa (Icom CI-V, Kenwood, Elecraft, Yaesu, FT-817 o TS-2000). Si en el programa eliges el modelo real, los comandos van directamente a la radio y funcionan todas sus funciones. Si eliges Kenwood TS-2000 funcionan las funciones comunes: frecuencia, modo, PTT y split. Con las radios Yaesu, la primera vez que un programa configurado como TS-2000 usa un puerto, el PTT puede no activarse en la primera transmisión: a partir de la segunda funciona, y el puerto lo recuerda.

Un programa por puerto: The Rigger ya los asigna para que nunca choquen. Cada radio tiene 4 puertos, que puedes subir hasta 16 en los ajustes.

### Ejemplos

- **WSJT-X**: *Ajustes › Radio*: Radio *Hamlib NET rigctl*, Servidor *127.0.0.1:4532*, PTT *CAT*.
- **Log4OM**: en la configuración CAT elige la radio *Kenwood TS-2000* en el puerto indicado para Log4OM. OmniRig ya no hace falta.
- **N1MM Logger+**: *Config › Configure Ports*: Radio *Kenwood TS-2000*, el puerto COM indicado para N1MM, cualquier velocidad, *DTR* y *RTS* desactivados.

## Ajustes

- **Idioma**: automático (el del sistema) o uno de los siete disponibles.
- **Inicio automático**: The Rigger arranca solo al encender el ordenador.
- **Actualizaciones automáticas**: las versiones nuevas se instalan solas, y solo cuando ningún programa está usando la radio.
- **Drivers USB automáticos**: los drivers USB que faltan se instalan solos.
- **Puertos por radio**: de 1 a 16. Se aplica al momento; los puertos en uso nunca se quitan.

## Drivers USB

- **Windows**: si conectas una radio sin driver, The Rigger descarga el driver oficial firmado desde Windows Update (o del fabricante) y lo instala. Windows pide una confirmación. Cubre Silicon Labs (Icom, Yaesu, Kenwood), FTDI (Elecraft y muchos cables), WCH CH340 (Xiegu y cables económicos) y Prolific.
- **macOS**: los drivers ya vienen con el sistema.

Los puertos COM virtuales de Windows usan el driver gratuito *com0com*, que The Rigger instala solo la primera vez (con una confirmación de Windows).

## Radios compatibles

- **Icom** y compatibles CI-V (también Xiegu): IC-7100, IC-7300, IC-705, IC-7610, IC-9700, IC-905, IC-7760 y otras.
- **Kenwood**: TS-2000, TS-480, TS-590S/SG, TS-890S, TS-990S.
- **Elecraft**: K3, KX2, KX3, K4.
- **Yaesu** recientes: FT-991/A, FTDX10, FT-710, FTDX101, FT-891, FTDX3000 y otras.
- **Yaesu** clásicas: FT-817, FT-818, FT-857, FT-897.
- Otras radios con comandos compatibles Kenwood: Lab599 TX-500, QRP Labs QDX/QMX y muchas SDR.

## Problemas frecuentes

- **La radio no aparece**: comprueba que esté encendida y conectada con el cable USB. En las Icom, la velocidad *CI-V USB* del menú de la radio debe estar en *Auto* o en un valor normal; *CI-V USB Echo Back* puede quedarse como está.
- **Un programa no se conecta**: pulsa **?** y comprueba que elegiste *Kenwood TS-2000* (o *Hamlib NET rigctl*) y el puerto correcto. Dos programas no pueden usar el mismo puerto serie.
- **La luz de un programa está amarilla**: el programa abrió el puerto pero no consulta la radio. Comprueba que el CAT esté activado en el programa.
- **Windows no crea los puertos COM**: en algunos PC con Windows 11 el driver *com0com* puede estar bloqueado. En ese caso usa la conexión *Hamlib NET rigctl*, que funciona siempre.

---

The Rigger · software desarrollado por IU1MVI · uso libre y gratuito para todos los radioaficionados. ¡73!
