# SecretDNS

**Herramienta gratuita para Windows que evita la vigilancia de Internet (DPI) con DNS sobre HTTPS y fragmentación SNI, activada con un solo clic.**

[English](README.md) · [한국어](README.ko.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md) · Español · [Português (Brasil)](README.pt-BR.md) · [Français](README.fr.md)

> Este documento es una traducción. Si hay alguna diferencia, la [versión en coreano](README.ko.md) es la que prevalece.

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%2F%2011-0078D4)
![License](https://img.shields.io/badge/license-Freeware-brightgreen)
[![Download](https://img.shields.io/badge/download-kilho.net-orange)](https://down.kilho.net/secretdns?lang=es)

![Pantalla de SecretDNS](images/secretdns-en.png)

## Descripción general

Al abrir un sitio web, el equipo envía dos cosas en texto plano: una **consulta DNS** que pide la dirección IP del sitio y el **nombre del sitio (SNI)** que viaja en el primer paquete de cada conexión HTTPS. Los equipos de inspección (DPI) de los operadores o administradores de red leen ambos para saber qué sitio visita y, si quieren, cortan la conexión o lo redirigen a una página de advertencia.

SecretDNS cierra ambos agujeros con una sola pulsación del **botón del candado**.

- **DNS** — Procesa las consultas DNS del equipo con **cifrado (DoH)** a través de un servidor como Cloudflare. No toca la configuración de red de Windows, así que al detener el programa todo vuelve a la normalidad al instante; y si el equipo se apaga de repente mientras está en ejecución, al reiniciar Internet funciona como siempre, sin dejar rastro.
- **SNI** — **Evita que el nombre del sitio quede expuesto a los equipos de inspección** en las conexiones HTTPS. La conexión al sitio funciona como siempre y, como solo se procesa la parte del nombre, apenas hay pérdida de velocidad.

Los sitios que dejan de funcionar al fragmentarse (bancos, pasarelas de pago) pasan intactos gracias a una **lista de excepciones** integrada, y en el **Informe** puede ver cómo se procesó cada sitio. Para los sitios que la evasión DNS no puede abrir — como el **error 451**, habitual en países sin libertad en Internet, donde el propio sitio rechaza las conexiones desde ese país — el **Proxy mixto** hace que solo esos sitios pasen por otro país. Solo los dominios que indique pasan por ahí, así que el resto de su Internet conserva toda su velocidad.

SecretDNS no es una VPN. No oculta su dirección IP ni cifra todo el tráfico: solo procesa los dos puntos que se usan para la vigilancia, DNS y SNI.

## Funciones principales

- **Un solo clic** — Basta con pulsar el **botón del candado** en la pantalla de inicio. Un clic en el icono de la bandeja o en el candado de la esquina superior derecha de Configuración también lo activa y desactiva.
- **DNS sobre HTTPS** — Cloudflare por defecto. Añada sus propios servidores y marque varios; SecretDNS cambia entre ellos automáticamente. También hay un modo **Servidores** que usa un servidor DNS sin cifrar (p. ej. 1.1.1.1).
- **Sin cambios en la configuración de Windows** — No se modifica la configuración DNS del adaptador de red. Al detener no queda rastro, y tras un corte de luz o un apagado forzado, al reiniciar todo vuelve a la normalidad.
- **Fragmentación SNI** — Evita que el nombre del sitio quede expuesto en conexiones HTTPS y HTTP.
- **Lista de excepciones / Lista manual** — Elija qué sitios no fragmentar, o solo cuáles fragmentar. Unos 160 dominios (bancos, pagos, portales, juegos …) vienen integrados como excepciones.
- **Solo navegadores** — Aplica la fragmentación solo a los navegadores principales, sin tocar juegos ni programas de trabajo. Activado desde el principio.
- **Paquete falso** — Un método de evasión adicional para las redes donde la fragmentación por sí sola no basta.
- **Conexión que no se corta** — Antes de iniciar comprueba que el servidor DNS es accesible; si el servidor deja de responder durante la ejecución, Internet no se corta y el cifrado se reanuda automáticamente cuando el servidor vuelve. Internet sigue funcionando tras la suspensión o un cambio de Wi-Fi.
- **Informe** — Tabla de dominios y resultado aplicado (cifrado, fragmentado, texto plano, vía servidor …), por separado para DNS y SNI, en una ventana aparte, con copia al portapapeles.
- **Proxy mixto** — Solo los dominios de la lista pasan por un servidor en el extranjero. Sirve para abrir sitios bloqueados con error 451 que el DNS no puede evadir; el resto conecta directamente como siempre, sin pérdida de velocidad.
- **Inicio automático · bandeja** — Ejecución al iniciar Windows; al cerrar la ventana pasa al área de notificación.
- **22 idiomas** — Sigue el idioma de visualización de Windows, y también puede elegirlo usted mismo en **Idioma** de Configuración.

## Descarga / Instalación

| Tipo | Enlace |
|---|---|
| Instalador | [Descargar](https://down.kilho.net/secretdns?lang=es) |
| Portable (ZIP) | [Descargar](https://down.kilho.net/secretdns?lang=es&nosetup) |

El instalador ejecuta SecretDNS al terminar y registra también **Ejecutar al iniciar**. Para la versión portable, descomprima el ZIP y ejecute `SecretDNS.exe`. En ambos casos SecretDNS pide **permisos de administrador**.

## Uso

### Primeros pasos

1. Inicie SecretDNS. Cuando aparezca la ventana de permisos de administrador, pulse **Sí**.
2. Pulse el **botón del candado** en el centro de la pantalla de inicio. Cuando el candado se ilumina en dorado, está en ejecución, y el icono del área de notificación (bandeja) también se vuelve dorado.
3. Use el navegador como siempre. No hay nada más que hacer.
4. Para desactivarlo, pulse de nuevo el candado o haga un clic en el icono de la bandeja. Al cerrar la ventana (×) el programa no se cierra, sino que va a la bandeja.

Qué se activa se decide en **Configuración**, que se abre con el botón del **engranaje** de la esquina superior derecha. Durante la ejecución la configuración queda bloqueada, así que deténgalo antes de cambiarla (**Idioma** y **Ver registro** siguen disponibles en ejecución). El candado de la esquina superior derecha de Configuración ejecuta y detiene directamente, así que no hace falta volver a la pantalla de inicio.

### Distribución de la pantalla

**Pantalla de inicio** — En el centro, el **botón del candado** (Ejecutar/Detener); arriba a la derecha, el **engranaje** (Configuración); y abajo, la versión en la barra de estado. Al pulsar el logotipo de arriba se abre la página web (el logotipo de las demás pantallas hace lo mismo).

**Configuración** — La flecha de arriba a la izquierda vuelve a la pantalla de inicio; el candado de arriba a la derecha ejecuta/detiene. El candado está abierto y gris cuando está detenido, y cerrado y dorado en ejecución.

| Elemento | Qué hace |
|---|---|
| **Configuración DNS** — Desactivado / Servidores / DNS sobre HTTPS | Cómo se procesan las consultas DNS. **Servidores** en las filas Servidores y DNS sobre HTTPS edita la lista de servidores correspondiente |
| **Configuración SNI** — Desactivado / Fragmento / Fragmentoⓜ | Fragmentar todos los sitios (salvo la lista de excepciones) o solo los de la lista manual |
| Lista **Excepción** / **Manual** | Al elegir Fragmento aparece la lista de excepciones debajo de esa fila; al elegir Fragmentoⓜ aparece la lista manual debajo de la suya. Un dominio por línea |
| **Habilitar proxy mixto** | Solo los dominios de la lista pasan por un servidor en el extranjero. Al marcarlo aparece justo debajo el cuadro de la lista (requiere una configuración DNS activa) |
| **Solo navegadores** | Aplica fragmentación y paquete falso solo al tráfico de los navegadores |
| **Habilitar paquete falso** | Método de evasión adicional para redes donde la fragmentación no basta |
| **Habilitar informe** + **Ver registro** | Guarda el informe. **Ver registro** abre la ventana del informe |
| **Ejecutar al iniciar** | Inicia en la bandeja al iniciar sesión. Si la última vez estaba en ejecución, también activa la protección automáticamente |
| **Idioma** | Idioma de la interfaz. Con **Sistema** sigue el idioma de visualización de Windows |

**Servidores DNS** — La lista del lado cuyo botón **Servidores** pulsó (Servidores o DNS sobre HTTPS) se muestra como tabla, con **Agregar** · **Editar** · **Eliminar** debajo.

**Ventana del informe** — Tres columnas: **Tipo** (DNS · SNI · VPN), **Dominio** y **Aplicado**. Cada línea idéntica se guarda una sola vez, y las líneas con la columna Aplicado vacía (enviadas sin procesar) se muestran atenuadas. **Copiar** / **Copiar(Todo)** copian texto separado por tabulaciones; **Borrar** vacía la lista. La ventana se puede redimensionar y, si oculta la ventana principal en la bandeja y la vuelve a abrir, la ventana del informe vuelve con ella.

**Icono de la bandeja** — Gris cuando está detenido, dorado en ejecución. Un clic alterna Ejecutar/Detener. El menú contextual tiene **SecretDNS** (mostrar ventana) · **Ejecutar** · **Detener** · **Kilho.net** · **Salir**. Al pasar el ratón se muestra la versión y el estado actual.

### Qué hacer cuando…

**Un sitio redirige a una página de advertencia o la conexión se corta**
Con la configuración por defecto (DNS **Servidores** o **DNS sobre HTTPS** + SNI **Fragmento**), basta con pulsar el candado para resolver la mayoría de los casos. Active el informe y entre en el sitio: la línea `SNI` debe decir **Fragmento** y la línea `DNS`, **Texto plano** o **DNS sobre HTTPS**. Si sigue sin funcionar, pruebe **Habilitar paquete falso** más abajo.

**Un sitio dejó de abrirse tras activar SecretDNS (banco, pago, inicio de sesión de un juego …)**
El tráfico de ese sitio no tolera la fragmentación. En Configuración, añada su dominio en una línea de la lista **Excepción**, debajo de la fila **Fragmento**, y vuelva a ejecutar.
- Escríbalo **empezando por un punto**, como `.example.com`, para que coincida con `example.com` y todos sus subdominios (`www.example.com`, `m.example.com`).
- Puede pegar la URL de la barra de direcciones tal cual: `https://`, `www.` y la ruta final se eliminan automáticamente.
- La lista se guarda al hacer clic fuera del cuadro, salir de Configuración o ejecutar, y se aplica **a partir de la siguiente ejecución**. Si ejecuta directamente con el candado de arriba a la derecha de Configuración, no hace falta volver a la pantalla de inicio.
- Unos 160 dominios — bancos, tarjetas, pagos, portales, compras, juegos, gobierno (`.go.kr`), escuelas (`.ac.kr`) — ya vienen integrados como excepciones, así que no hace falta escribirlos. Siguen funcionando aunque vacíe la lista.

**Fragmentar solo unos pocos sitios y no tocar el resto**
Cambie la configuración SNI a **Fragmentoⓜ** y debajo de esa fila aparece el cuadro de la lista **Manual**. Solo se fragmentan los dominios escritos aquí; todo lo demás se envía intacto. Si solo le dan problemas uno o dos sitios, esta opción es más segura. Las reglas de escritura son las mismas que en la lista de excepciones y, si la lista está vacía, SecretDNS le pide que escriba un dominio antes de ejecutar.

**Cifrar solo el DNS, sin fragmentación**
Ponga la configuración DNS en **DNS sobre HTTPS** y la SNI en **Desactivado**. Al contrario, para dejar el DNS como está y usar solo la fragmentación, ponga DNS en **Desactivado**. Con ambos desactivados aparece "No hay funciones para ejecutar.".

**Aparece "No se puede conectar al servidor DNS cifrado (DoH)."**
Algunas redes de empresas o centros educativos tienen Internet pero no llegan a ciertos servidores DoH. Hay dos opciones:
- Pulse **Servidores** en la fila DNS sobre HTTPS y marque otro servidor de la lista (por ejemplo **cloudflare-dns.com** de la lista por defecto).
- O cambie la configuración DNS a **Servidores**. Sin cifrado, pero conserva el efecto de usar otro servidor DNS sin cambiar la configuración de Windows.

**Usar otro servidor DNS**
Pulse **Servidores** en la fila **Servidores** o **DNS sobre HTTPS** de la configuración DNS para abrir esa lista de servidores.
- Con **Agregar** introduzca **Nombre · Dirección 1 · Dirección 2** (de reserva, puede dejarse vacía). Los servidores llevan una dirección IPv4 como `8.8.8.8`; DoH lleva una dirección como `https://1.1.1.1/dns-query` o `https://dns.google/dns-query`.
- Solo se usan los servidores **marcados**. Si marca varios, cuando uno no responde se pasa automáticamente a otro. Si no marca ninguno, se usa Cloudflare.
- La lista por defecto incluye Cloudflare (marcado) y Google (sin marcar).
- Los cambios se aplican **a partir de la siguiente ejecución**.

**No afectar a juegos ni programas de trabajo**
Mantenga activado **Solo navegadores** (viene activado desde el principio). La fragmentación y el paquete falso se aplican solo al tráfico de los navegadores principales como Chrome · Edge · Firefox · Whale; los demás programas no se tocan. El procesamiento DNS sigue aplicándose sea cual sea el programa.
Al contrario, si un programa que no es un navegador (un gestor de descargas, por ejemplo) también necesita fragmentación, desactive **Solo navegadores**.

**Sigue bloqueado incluso con fragmentación**
Pruebe **Habilitar paquete falso**. Es un método de evasión adicional para los equipos de inspección que la fragmentación por sí sola no consigue superar, y no afecta a la conexión real.

**Abrir sitios bloqueados pasando solo esos por un servidor en el extranjero (Proxy mixto)**
En los países donde no está garantizada la libertad en Internet, un sitio puede rechazar por completo las conexiones procedentes de ese país y el navegador muestra un **error 451** (Unavailable For Legal Reasons). Es algo raro en los países con Internet libre. En ese caso ni el cifrado DNS ni la fragmentación lo abren, porque el bloqueo se basa en el país desde el que se conecta. El proxy mixto hace que solo esos sitios pasen por un servidor de otro país.
Con una configuración DNS activa, marque **Habilitar proxy mixto** y justo debajo aparece el cuadro de la lista. Escriba un dominio por línea (`.example.com`, misma regla que la lista de excepciones) y ejecute.
- Solo los dominios de la lista pasan por el servidor en el extranjero; el resto conecta directamente como siempre. A diferencia de una VPN completa, los demás sitios conservan su velocidad.
- El servidor se asigna automáticamente en cada ejecución y, si no responde, se pasa automáticamente al siguiente.
- En el informe queda como tipo **VPN**, aplicado **Vía servidor**.
- El proxy mixto requiere una configuración DNS activa y se desactiva junto con ella al poner DNS en Desactivado.

**Tenerlo activado cada vez que se enciende el equipo**
Marque **Ejecutar al iniciar** (el instalador ya lo registra). Al iniciar sesión arranca en la bandeja sin ventana y, **si la última vez lo dejó en ejecución**, también activa la protección automáticamente. Si lo detuvo y salió usted mismo, en el siguiente arranque no se activa y queda a la espera.
Si el Wi-Fi tarda en conectarse tras el arranque, se inicia automáticamente en cuanto hay red.

**Mantenerlo activo después de cerrar la ventana**
Al pulsar cerrar (×) no se cierra, sino que va a la bandeja, así que no hay nada que configurar. Para salir del todo, clic derecho en el icono de la bandeja → **Salir** (aparece una confirmación). Al salir, la protección también se desactiva.

**Cambiar el idioma de la interfaz**
Elija uno en **Idioma**, al final de Configuración, y la pantalla cambia a ese idioma al instante. También se puede cambiar en ejecución. Elija **Sistema** para volver a seguir el idioma de visualización de Windows.

**Ver cómo se está procesando cada sitio ahora mismo**
Active **Habilitar informe** y abra la ventana del informe con **Ver registro**. Los dominios visitados durante la ejecución se van añadiendo línea a línea. **Ver registro** también se puede pulsar en ejecución.

| Tipo | Aplicado | Significado |
|---|---|---|
| DNS | **DNS sobre HTTPS** | Consultado a través del servidor cifrado |
| DNS | **Texto plano** | Consultado a través del servidor indicado (sin cifrado) |
| SNI | **Fragmento** | El nombre del sitio se envió fragmentado |
| SNI | (vacío) | Enviado sin procesar: el sitio está en la lista de excepciones |
| VPN | **Vía servidor** | Pasó por el servidor en el extranjero mediante el proxy mixto |

Con **Copiar(Todo)** puede pegarlo en el Bloc de notas o Excel con las columnas separadas.

**Por qué Internet no se corta aunque el servidor DNS no responda**
SecretDNS comprueba antes de ejecutarse que el servidor DNS es accesible y, si durante la ejecución el servidor deja de responder un tiempo, lo gestiona automáticamente para que Internet no se detenga. Cuando el servidor vuelve, regresa automáticamente al funcionamiento normal; mientras tanto, el estado se ve en el icono de la bandeja y en el informe. No hace falta volver a ejecutarlo tras salir de la suspensión o cambiar de Wi-Fi.

**Aparece un aviso sobre el controlador**
En raras ocasiones puede aparecer un aviso pidiendo reiniciar el equipo antes de ejecutar. Basta con reiniciar como se indica.

**El equipo se apagó durante la ejecución**
No hay de qué preocuparse. SecretDNS no cambia la configuración de red de Windows y solo actúa mientras está en ejecución, así que tras un corte de luz o un apagado forzado, al encender de nuevo Internet funciona como siempre. Con Ejecutar al iniciar activado, vuelve a iniciarse solo tras iniciar sesión.

## Configuración

Se cambia en **Configuración** y se guarda al instante. La mayoría se aplica **a partir de la siguiente ejecución**, y la configuración se conserva al actualizar.

| Elemento | Por defecto (instalador) | Por defecto (portable) |
|---|---|---|
| Configuración DNS | Servidores | Servidores |
| Configuración SNI | Fragmento | Fragmento |
| Lista de servidores DNS | Servidores: Cloudflare ✓, Google / DNS sobre HTTPS: Cloudflare ✓, cloudflare-dns.com ✓, Google | igual |
| Habilitar proxy mixto | Desactivado | Desactivado |
| Solo navegadores | Activado | Activado |
| Habilitar paquete falso | Desactivado | Desactivado |
| Habilitar informe | Desactivado | Desactivado |
| Ejecutar al iniciar | Activado | Desactivado |
| Idioma | Sistema | Sistema |

El idioma de la interfaz sigue el idioma de visualización de Windows (22 idiomas; en otro caso, inglés) y se puede cambiar en **Idioma** de Configuración.

## Requisitos

- Windows 10 o Windows 11 (32 y 64 bits)
- **Permisos de administrador** — en cada inicio aparece una ventana de confirmación de permisos.
- No se necesita ningún runtime adicional.
- Conexión a Internet — para la comprobación del servidor DNS y los avisos de nueva versión.

## Actualizaciones

SecretDNS **no** se actualiza solo. Al iniciarse comprueba si hay una versión nueva y muestra un aviso; al pulsar **Sí** se abre la página de descarga y el programa se cierra. Las nuevas versiones se publican manualmente tras una verificación interna y se anuncian en la [página de SecretDNS](https://kilho.net/secretdns). Consulte el [aviso sobre la política de actualizaciones](https://en.kilho.net/archives/notice/2940).

## Licencia

SecretDNS es **freeware**. Puede usarlo gratis y sin restricciones en cualquier lugar — empresa, casa, organismos públicos, escuela — y redistribuirlo libremente.

## Enlaces

- Sitio web: <https://kilho.net/secretdns>
- Foro: <https://kilho.top/forum/qna>
- X (Twitter): <https://www.twitter.com/kilhonet>

© KILHO.NET
