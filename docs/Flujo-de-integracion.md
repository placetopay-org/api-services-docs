# Flujo de integracion

1. Una vez se capture el número de tarjeta del usuario se realiza el consumo al servicio de
información (informationRequest) enviándolo en la petición

2. Se analiza la respuesta del servicio para disponer las opciones que siguen
-  Si la respuesta trae tipos de crédito “credits” se deben mostrar al usuario para
permitirle seleccionar cual desea usar.
- Si la respuesta tiene el parámetro “displayInterest” en true, se debe, una vez
seleccionado un tipo de crédito, consumir el servicio de cálculo de intereses
(interestCalculation) y mostrar al usuario la respuesta, así cada vez que el usuario
cambie de tipo de crédito.
- Si la respuesta trae el parámetro “requireOtp” en true, se debe hacer el consumo
al servicio de generación de OTP (otpGeneration) y obtener del usuario el código
que será de 6 dígitos para enviarlo posteriormente en el servicio de validación de 
OTP (otpValidate) una vez se tenga una respuesta se enviará el resultado
signature bajo el campo OTP de la solicitud de procesamiento.

3.  Una vez se haya obtenido el tipo de crédito (si lo hay), el OTP (si se requiere) se consume
el servicio de procesamiento de transacción (processTransaction) y se analiza la respuesta
que puede ser final (aprobada, declinada o fallida) o que puede estar pendiente. En
ambos casos se retornará un valor para internalReference que es muy importante
almacenar porque le permitirá realizar consultas posteriores con el servicio
(queryTransaction).
- Si se aprobó la transacción es importante almacenar también el número de
autorización, le permitirá realizar reversos posteriormente si fuese necesario.
- Generalmente las transacciones son culminadas en un tiempo corto (menos de 3
seg), pero si la transacción queda en estado pendiente es importante tener un
cron job o similar que esté consultando cada 5 minutos por las transacciones
pendientes hasta que se resuelvan.

# Información adicional

La conexión API de Placetopay es usada en diferentes paises, por lo que el uso de elementos como “credits”, “displayInterest”, “requireOtp” y "MPIlookUp" dependerá si en el pais en el cual realizas la integración cuenta con estos mecanismos.