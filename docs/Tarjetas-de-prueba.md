## Números de tarjeta de pruebas

Es importante definir que estas tarjetas solo tienen dicho comportamiento en el ambiente de pruebas

En todos los casos excepto donde se especifique el CVV y la fecha de expiración puede ser cualquiera con tal de que sea vigente para que su comportamiento aplique.

Para las pruebas con 3DS en el comportamiento se describe su resultado

* **Y**: Autenticado sin fricción
* **C**: Solicita challenge
* **A**: Responde con attempt
* **N**: No autenticado

Franquicia | Número | Comportamiento
---------|----------|---------
Diners | 36545400000008 | Aprueba
Diners | 36545400000248 | Rechaza
Diners | 36545400000701 | Deja la transacción en procesamiento manual y si se procesa queda en estado aprobado
Diners | 36545407030701 | Deja la transacción en estado pendiente y se resuelve a rechazado
Diners | 36545407032814 | Arroja una excepción en el proceso
Diners | 36545400000438 | Se tarda 180 segundos en responder y queda en estado aprobado
Diners | 36545407032780 | Deja la transacción en procesamiento manual y si se procesa queda en estado aprobado
Diners | 36545407032806 | Deja la transacción en estado pendiente y se resuelve a aprobado
Diners | 36545407032848 | Aprueba
Visa | 4110760000000008 | Aprueba **3DS-C**
Visa | 4110760000000016 | Rechaza
Visa | 4110760000000032 | Deja la transacción en estado pendiente y se resuelve a aprobado **3DS-C**
Visa | 4110760000000040 | Deja la transacción en estado pendiente y se resuelve a rechazado **3DS-A**
Visa | 4048370000000037 | Deja la transacción en estado pendiente y se resuelve a rechazado
Visa | 4110760000000073 | Deja la transacción en estado pendiente y se resuelve a aprobado
Visa | 4110760000000065 | Arroja una excepción en el proceso **3DS-N**
Visa | 4110760000000024 | Se tarda 180 segundos en responder y queda en estado aprobado
Visa | 4110760000000115 | Se tarda 180 segundos en responder y queda en estado rechazado
Visa | 4110760000000057 | Aprueba si el monto es inferior a 200USD de lo contrario rechaza
Visa | 4110760000000081 | Aprueba
Visa | 4012888888881881 | Aprueba si se proporciona la expiración 11/28 y el cvv 917 de lo contrario rechaza
Visa | 4381080000000003 | Deja la transacción en estado pendiente y se resuelve a rechazado
Visa | 4005580000000040 | Rechaza
Visa | 4110770010002837 | Aprueba
Visa | 4111111111111111 | Aprueba **3DS-Y**
Visa | 4509564638437551 | Deja la transacción en estado pendiente y se resuelve a aprobado
Visa | 4864921336824366 | Deja la transacción en estado pendiente y se resuelve a rechazado
Visa | 4931974429847108 | Deja la transacción en estado pendiente y se resuelve a rechazado
Visa | 4716375184092180 | Rechaza
Visa | 4532034637206853 | Deja la transacción en procesamiento manual y si se procesa queda en estado rechazado
Visa | 4212121212121214 | Deja la transacción en procesamiento manual y si se procesa queda en estado aprobado
Visa | 4666666666666669 | Se tarda 180 segundos en responder y queda en estado aprobado
Mastercard | 5180300000000005 | Aprueba **3DS-Y**
Mastercard | 5180300000000039 | Rechaza **3DS-N**
Mastercard | 5180300000000047 | Deja la transacción en estado pendiente y se resuelve a aprobado **3DS-C**
Mastercard | 5180300000000054 | Deja la transacción en estado pendiente y se resuelve a rechazado **3DS-A**
Mastercard | 5292594382060745 | Aprueba **3DS-C**
American Express | 376651001281274 | Aprueba si se proporciona la expiración 06/36 y el cvv 4637 de lo contrario rechaza
Discover | 6550590000000001 | Aprueba
Discover | 6550590000000019 | Rechaza
Discover | 6550590000000027 | Deja la transacción en estado pendiente y se resuelve a aprobado
Discover | 6550590000000035 | Deja la transacción en estado pendiente y se resuelve a rechazado
Maestro | 6759649826438453 | Aprueba
Discover | 6557351234543156 | Aprueba
Discover | 6557351234543164 | Rechaza
Mastercard | 5367680000000005 | Aprueba
Mastercard | 5367680000000013 | Rechaza
Visa | 4381080000000029 | Aprueba
Visa | 4381080000000011 | Rechaza
Somos | 8810060001592705 | Aprueba
Exito | 5903090000000000 | Aprueba
Alkosto | 5903120000000000 | Aprueba
Comfandi | 9391111111111111 | Aprueba
Comfandi | 9395555555555555 | Rechaza
Mefia | 6377470102391155 | Aprueba si se proporciona la expiración 12/24
Mefia | 6377470107014851 | Rechaza
Mefia | 6377470106963215 | Aprueba
Mefia | 6377470100506457 | Aprueba
Mefia | 6377470105684614 | Deja la transacción en estado pendiente y se resuelve a aprobado
Mefia | 6377470106813436 | Deja la transacción en estado pendiente y se resuelve a rechazado
Mefia | 6377470106672139 | Rechaza
Tarjeta ATH | 0215020177972730 | Aprueba
Tarjeta ATH | 2215714777972730 | Aprueba
Tarjeta ATH | 0215025888083941 | Deja la transacción en estado pendiente y se resuelve a rechazado
Tarjeta ATH | 2215716999194052 | Deja la transacción en estado pendiente y se resuelve a aprobado
Tarjeta ATH | 0215027111105163 | Deja la transacción en estado pendiente y se resuelve a rechazado
Tarjeta ATH | 2215719446775653 | Arroja una excepción en el proceso
Tarjeta ATH | 0215026116775785 | Rechaza

## Códigos postales disponibles para prueba de AVS

Para realizar un proceso exitoso usa 55555 como código postal

ZIP Code | Comportamiento
---------|----------
55555 | Retorna transacccion aprobada con AVS exitoso (Y)
44444 | Retorna transaccion aprobada con AVS fallido (A) y reversa la transacción
33333 | Retonra transaccion aprobada con AVS fallido (A) rechaza el reverso. Pero cuando se consulta el reverso fue exitoso

## OTP para casos de prueba

Para que el proceso de OTP sea exitoso en el proceso de validación de OTP de estos servicios, cualquier otro código es un rechazo

* 123456
* 000000

## OTP en 3DS

Cuando la autenticación de 3DS requira challenge (OTP) el código aceptado es **12345**