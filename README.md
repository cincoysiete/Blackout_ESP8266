# 📘 Manual de Usuario
## Sistema de Supervisión: ESP8266 + Pantalla TFT + Servidor PHP + Telegram

---

## 🖐 Introducción

Este manual está diseñado para que cualquier usuario comprenda el funcionamiento general del sistema de monitoreo basado en **ESP8266 con pantalla de 0.9”** y servidor web PHP, incluyendo su integración con **Telegram**.

El sistema permite detectar cortes de energía, pérdidas de conexión WiFi o fallos en la red, notificando en tiempo real al usuario por medio de:
- Mensajes automáticos al servidor PHP.
- Notificaciones en Telegram.
- Información visual en la pantalla TFT.

---

## 🏠 Situaciones y Mensajes del Sistema

| Situación                   | Acción de la ESP8266            | Acción del Servidor / Telegram |
|-----------------------------|---------------------------------|---------------------------------|
| Energía y WiFi OK          | Envía `conectado` al servidor   | El servidor registra `conectado` y opcionalmente notifica. |
| WiFi Desconectado           | Muestra "Sin WiFi" en pantalla  | No puede enviar datos hasta recuperar conexión. |
| Corte de Energía detectado  | Envía `noluz-` al servidor      | El servidor puede reenviar alerta a Telegram. |
| Recuperación de energía     | Envía `conectado` al servidor   | El servidor puede notificar en Telegram la recuperación. |

---

## 👀 Información que Muestra la Pantalla

- **Conexión OK:** Estado "WiFi Conectado" y hora del último envío.
- **Sin WiFi:** Mensaje de alerta "Sin conexión WiFi".
- **Corte de Energía:** Indicador de fallo y posible mensaje si es detectado antes del apagado.

La pantalla sirve como primer punto de diagnóstico local para que el usuario pueda actuar rápidamente.

---

## 💻 Información que Muestra el PHP

- Recibe los mensajes `conectado`, `nowifi-` y `noluz-` desde la ESP8266.
- Puede guardar un historial de eventos.
- Puede mostrar en tiempo real el último estado recibido.
- Puede ejecutar código adicional para notificar por **Telegram** cuando:
  - Se detecte `noluz-` (corte de energía).
  - Se detecte `nowifi-` (fallo de conexión).
  - Se recupere la conexión (`conectado`).

---

## 🧑‍🔧 Opciones de Configuración mediante Formulario Web

La ESP8266 cuenta con un sistema de configuración accesible a través de su dirección IP desde cualquier navegador web.

Al acceder, el usuario encontrará un **formulario de configuración** que permite:

- Introducir los datos de la red WiFi:
  - Nombre de la red (SSID).
  - Contraseña WiFi.

- Configurar los datos de notificación:
  - Token de Telegram.
  - ID de Chat de Telegram.
  - Dirección URL del servidor PHP donde enviar los estados.

- Personalizar mensajes que serán enviados:
  - Mensaje cuando se pierde la energía.
  - Mensaje cuando se pierde la conexión WiFi.
  - Mensaje cuando se recupera la conexión.

- Definir temporizadores:
  - Intervalo de tiempo para reintentos de conexión.
  - Tiempo entre envíos de estado.

Una vez enviados, estos datos se guardan en la memoria interna de la ESP8266 y permanecen configurados incluso después de reiniciar el dispositivo.

---

## 🚀 Beneficios de Implementar Este Proyecto

- ⚡ **Supervisión en Tiempo Real**: Sabrás al instante si tu sistema ha perdido energía o conexión.
- 🚨 **Alertas Inmediatas**: Recibirás notificaciones automáticas en **Telegram** sin necesidad de revisar manualmente.
- 📊 **Registro de Eventos**: El servidor puede almacenar todas las alertas, facilitando el análisis de incidencias.
- 👀 **Visualización Local**: La pantalla te permite comprobar el estado sin depender de otros dispositivos.
- 🔗 **Escalable y Adaptable**: Puedes conectar múltiples ESP8266 al mismo servidor para cubrir diferentes zonas.
- ⚙️ **Configuración Flexible**: Ajusta todos los parámetros de funcionamiento sin reprogramar la placa, desde cualquier navegador.

---

## 🧠 Conclusión

El sistema permite tanto monitoreo local como remoto, con avisos claros y automáticos cuando:
- Hay un corte de energía.
- Se pierde la conexión a Internet.
- Se recupera el servicio.

De esta forma siempre estarás informado de lo que ocurre, y podrás actuar rápidamente si algo va mal, mejorando la seguridad y fiabilidad de tus instalaciones.

---

![S3590cd3747434bdead931e3ae90ee80cG](https://github.com/user-attachments/assets/6c959965-4735-461a-8c0e-a7554731e29c)
