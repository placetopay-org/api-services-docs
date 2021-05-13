---
tags: [Crear sesión]
---


# Tipos de documento

Al momento de solicitar crear una sesión, si usa alguna de las estructuras `payer`, `buyer` o `shipping` deberá enviar en el atributo **`DocumentType`** alguno de los siguientes códigos  dependiendo del pais:

```json
AVISO IMPORTANTE:

Según  del tipo de documento enviado el sistema realizará la valdiación basado en  expresiones regulares 
```


### Global


Código| Tipo de documento | Regla de validación
---------|----------|----------
 PPN	 | Pasaporte | `'/^[a-zA-Z0-9_]{4,16}$/'`
 TAX | TAX | `'/^[a-zA-Z0-9_]{4,16}$/'`
 LIC | Labeler Identification Code | `'/^[a-zA-Z0-9_]{4,16}$/'`

### Colombia

Código| Tipo de documento | Regla de validación
---------|---------- |----------
 CC | Cédula de ciudadanía  | `'/^[1-9][0-9]{3,9}$/'`
 CE | Cédula de extranjería | `'/^([a-zA-Z]{1,5})?[1-9][0-9]{3,7}$/'`
 TI | Tarjeta de identidad| `'/^[1-9][0-9]{4,11}$/'`
 NIT | Número de Identificación Tributaria|` '/^[1-9]\d{6,9}$/'`
 RUT | Registro único tributario| `'/^[1-9]\d{6,9}$/'`
 
### Ecuador

Código| Tipo de documento | Regla de validación
---------|----------|---------
 CI | Cédula de identidad|`'/^\d{10}$/'`
 RUC | Registro Único de Contribuyentes|`'/^\d{13}$/'`
 

### Costa Rica

Código| Tipo de documento | Regla de validación
---------|----------|------------
 CRCPF | Cédula personal física |`'/^[1-9][0-9]{8}$/'`
 CPJ | Cédula personal juridica |`'/^[1-9][0-9]{9}$/'`
 DIMEX | DIMEX- Docuemnto de identificación de Migración y Extranjería|`'/^[1-9][0-9]{10,11}$/'`
  DIDI | DIDI - Docuemnto de identificación de diplomáticos|`'/^[1-9][0-9]{10,11}$/'`

### Chile

Código| Tipo de documento | Regla de validación
---------|----------|------------
 CLRUT | Cédula personal física |`'/^(\d{1,2}(?:\.?\d{1,3}){2}-[\dkK])$/'`


### Panamá

Código| Tipo de documento| Regla de validación
---------|----------|------------
 CIP | Cédula de identidad personal| `/^(N,E,PE\d+)?\d{2,6}\d{2,6}$/`

 ### Brasil

 Código| Tipo de documento| Regla de validación
---------|----------|------------
 CPF | Cadastro de Pessoas Físicas|`'/^\d{10,11}$/'`


 ### Perú 

  Código| Tipo de documento| Regla de validación
---------|----------|------------
 DNI | DNI|`'/^\d{8}$/'`



