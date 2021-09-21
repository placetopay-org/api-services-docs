# PinPad

Un PINPAD es un dispositivo electrónico que se utiliza en una transacción de débito, crédito o tarjeta inteligente para aceptar y cifrar el número de identificación personal (PIN) del titular de la tarjeta.

Esta API proporciona un servicio PinPad con generación de PinBlock cifrada según ISO 9564.


## Flujo de generación de PinPad
### Servició de generación de transacción
Este servicio permite generar una transaccion en el servicio de pinpad, utilizando la autenticacion de sitios, El Sitio autenticado nos entrega el token asociado al sitio en el servicio de pinpad.

La autenticación al servicio debe ser enviada sobre el objeto `auth`, el cual debe contener los atributos descritos en el modelo Authentication

Valor | Descripción
---------|----------
 **login** | Identificador del sitio. 
 **tranKey** | Valor formado por la siguiente operación: `Base64(SHA-256(nonce + seed + secretkey))`. (El nonce dentro de la operación es el original, es decir, el que no está en Base64.)
 **nonce** | Valor aleatorio para cada solicitud codificado en Base64. 
 **seed** | Fecha actual, la cual se genera en formato ISO 8601. 

De la misma manera, el instrumento de pago debe ser enviado sobre el objeto `instrument`. 

#### Pago con tarjeta

Valor | Descripción
---------|----------
 **card** | Objeto con la información que identifica el instrumento de pago. 
 **number** | Numero identificador de la tarjeta


```json
{
  "auth": {
    "login": "c4ca4238a0b923820dcc509a6f75849b",
    "tranKey": "2lCqMqRbJ\/OcjSjlK32aVDDlL7dwhA\/bl9i2CnZUvdE=",
    "nonce": "NjE0MjI0Y2YyYTcyOQ==",
    "seed": "2021-09-15T11:52:31-05:00"
  },
  "instrument": {
    "card": {
      "number": "4111111111111111"
    }
  }
}

```

#### Pago con Token

Valor | Descripción
---------|----------
 **token** | Identificador del metodo de pago


```json
{
  "auth": {
    "login": "c4ca4238a0b923820dcc509a6f75849b",
    "tranKey": "2lCqMqRbJ\/OcjSjlK32aVDDlL7dwhA\/bl9i2CnZUvdE=",
    "nonce": "NjE0MjI0Y2YyYTcyOQ==",
    "seed": "2021-09-15T11:52:31-05:00"
  },
  "instrument": {
    "token": {
      "token": "6b453cb884aa34014b01e9c5845364e40e53abc850cb7b92c9b46264e7f71452"
    }
  }
}

```
#### Respuesta del servicio

```json
{
  "status": {
    "status": "APPROVED",
    "reason": "00",
    "message": "Aprobada",
    "date": "2021-09-14T17:43:48-05:00"
  },
  "data": {
    "pinPad": {
      "positions": "7915864032",
      "transactionId": "b0c62f97-3b06-4c33-b68f-e281e95eb4bb",
    }
  }
}
```

### Servicio de generación de PinBlock
Permite generar el pinblock con una transaccion en base a las posiciones entregadas por el usuario.

De la misma manera del servicio anterior, La autenticación al servicio debe ser enviada sobre el objeto `auth`. Adicionalmente debe incluir los siguiente datos en el instrumento `pinPad`:

Valor | Descripción
---------|----------
 **positions** | Pin en posiciones entregadas por el usuario.
 **transactionId** | Identificador de la transacción en PinPad


```json 
{
   "instrument": {
     "pinPad": {
       "positions": "4235",
       "transactionId": "b0c62f97-3b06-4c33-b68f-e281e95eb4bb",
    }
  }
}
```

#### Respuesta del servicio

```json
{
  "status": {
    "status": "APPROVED",
    "reason": "00",
    "message": "Aprobada",
    "date": "2021-09-14T17:43:48-05:00"
  },
  "data": {
    "pinPad": {
      "positions": "4235",
      "transactionId": "b0c62f97-3b06-4c33-b68f-e281e95eb4bb",
      "pinBock": "106C56A4819B68EA"
    }
  }
}
```

