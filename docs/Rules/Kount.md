---
stoplight-id: gwygp6jg6qxqi
---

# Kount

## ¿Qué es?
Kount es una plataforma avanzada de prevención de fraude y gestión de riesgos que utiliza inteligencia artificial para proteger a las empresas contra actividades fraudulentas en transacciones en línea. Analiza en tiempo real los datos transaccionales para identificar y bloquear posibles fraudes, optimizando la experiencia del cliente y reduciendo pérdidas financieras. Esta solución es crucial para sectores como el comercio electrónico y servicios financieros.

## ¿Cómo integrar Kount?
[Como generar id de sesión para el device data collector](https://developer.kount.com/hc/en-us/articles/4411121644820-How-to-Create-a-Session-ID-for-the-Device-Data-Collector-DDC-)

Después de registrarte para los servicios de Kount y recibir un ID de cliente, agrega el SDK del Cliente Web a tu sitio web para integrar el Colector de Datos del Dispositivo.

Para mas información ver documentación: [How to Integrate the Web Client SDK for Device Data Collection into Your Website – Kount Developer](https://developer.kount.com/hc/en-us/articles/6731598562836-How-to-Integrate-the-Web-Client-SDK-for-Device-Data-Collection-into-Your-Website)


## Crear sesión kount

[Device Data Collector](https://developer.kount.com/hc/en-us/articles/6731598562836-How-to-Integrate-the-Kount-Web-Client-for-Device-Data-Collection-into-Your-Website)

Para crear la sesión kount debe generase con los datos clientId= 201000, Environment=TEST (sandbox) o Environment=PROD (production) una vez obtenida la conexión Data device collector (DDC) enviar el kount sesión en el objeto kount.

```json
{
  ...
  "kount": {
    "session": "ba2ccc0c27d84921ae9034da92ebc74d"
  }
  ...
}
```