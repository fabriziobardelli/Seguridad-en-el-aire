# Seguridad-en-el-aire
Cómo sobrevivir a una Wi-Fi pública

# Auditoría de Seguridad — Análisis de navegación HTTP en una red Wi-Fi pública

## 1. Introducción

El objetivo de esta auditoría es analizar los riesgos asociados a la navegación por HTTP, especialmente al utilizar una red Wi-Fi pública. Para ello, se observó una solicitud HTTP en las herramientas de desarrollador del navegador, identificando la URL solicitada, el método HTTP, el host y los headers enviados.

El análisis permite comprender qué información puede quedar expuesta cuando una comunicación no utiliza cifrado y cuáles son las medidas que pueden aplicarse para reducir estos riesgos.

## 2. Sitio analizado → http://neverssl.com

La solicitud fue analizada mediante las herramientas de desarrollador del navegador, específicamente en la sección **Network/Red → Headers**.
Durante el análisis de la solicitud HTTP se pudieron identificar los siguientes elementos:

* **URL:** Request URL   `http://shinysublimegoodpathway.neverssl.com/online/`
* **Método HTTP:** Request method `GET`
* **Host:** `shinysublimegoodpathway.neverssl.com`
* **Protocolo utilizado:** `HTTP/1.1 `
* **Headers:** `GET /online/ HTTP/1.1`  
`Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7`  
`Accept-Encoding: gzip, deflate`  
`Accept-Language: es-AR,es;q=0.9`  
`Cache-Control: no-cache`  
`Connection: keep-alive`  
`Host: quietfinewonderfulmagic.neverssl.com`  
`Referer: http://neverssl.com/`  
`Upgrade-Insecure-Requests: 1`  
`User-Agent: Mozilla/5.0 (iPad; CPU OS 18_5 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/18.5 Mobile/15E148 Safari/604.1`

Los headers pueden contener información relevante sobre la comunicación, como `User-Agent`, `Referer`, cookies y otros parámetros.

Al utilizar HTTP, esta información puede viajar sin cifrado como texto plano, dependiendo del contenido concreto de la solicitud.

## 3. Riesgos encontrados

El principal riesgo identificado es la **falta de cifrado propia de HTTP**. En una red Wi-Fi pública, un atacante que consiga observar el tráfico podría llegar a interceptar determinada información transmitida entre el dispositivo y el servidor.

Entre los posibles datos expuestos se encuentran:

* URLs y páginas solicitadas.
* Headers HTTP.
* Cookies de sesión, si son transmitidas sin protección.
* Información enviada mediante formularios.
* Credenciales, si fueran enviadas mediante una conexión HTTP.
* Contenido de las respuestas del servidor.

Además de observar el tráfico, un atacante situado en una posición adecuada podría intentar **modificar determinadas comunicaciones**.

Por este motivo, las redes Wi-Fi públicas deben considerarse redes no confiables y se recomienda evitar el envío de información sensible dentro de conexiones HTTP.

## 4. ¿Cómo ayuda una VPN?

Una VPN agrega una capa adicional de seguridad al establecer un **túnel cifrado** entre el dispositivo del usuario y el servidor VPN.

Esto permite:

* **Cifrado:** dificulta que otros usuarios de la red Wi-Fi puedan leer el tráfico que circula entre el dispositivo y el servidor VPN.
* **Túnel seguro:** los datos viajan encapsulados dentro de una conexión protegida hasta el servidor VPN.
* **Protección del tráfico:** reduce el riesgo de que un atacante conectado a la misma red pública pueda observar directamente el contenido del tráfico.
* **Privacidad:** los sitios web normalmente reciben la dirección IP del servidor VPN en lugar de la IP pública original del usuario.

Sin embargo, una VPN **no reemplaza HTTPS**. Lo recomendable es utilizar ambos mecanismos: HTTPS para proteger la comunicación entre el navegador y el sitio web, y una VPN para proteger el tráfico entre el dispositivo y el servidor VPN, especialmente al utilizar redes públicas.

## 5. Tres Reglas de Oro

### 1. Utilizar protocolos HTTPS

Verificar SIEMPRE que los sitios utilicen `https://`, especialmente antes de ingresar información sensible como contraseñas, datos bancarios o información personal.

### 2. Utilizar una VPN en redes públicas y verificar el nombre de la red.

Una VPN permite cifrar el tráfico y establecer un túnel seguro, reduciendo los riesgos asociados a las redes Wi-Fi públicas, además de confirmar con el establecimiento cuál es su Wi-Fi oficial para evitar redes falsas creadas para engañar a los usuarios.

### 3. Evitar operaciones sensibles en redes desconocidas

No realizar operaciones bancarias ni introducir información confidencial cuando no sea necesario. Además, se recomienda mantener actualizado el sistema, desactivar la conexión automática a redes desconocidas y utilizar autenticación multifactor.

## 6. Conclusión

El análisis demuestra que utilizar HTTP en una red Wi-Fi pública puede representar un riesgo debido a la ausencia de cifrado en la comunicación. Información como URLs, headers, cookies o datos enviados mediante formularios podría quedar expuesta ante un atacante capaz de interceptar el tráfico.

El uso de HTTPS, complementado con una VPN y buenas prácticas de seguridad, permite reducir significativamente estos riesgos y mejorar la protección de la información durante la navegación en redes públicas.
