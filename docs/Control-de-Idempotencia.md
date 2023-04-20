# Control de Idempotencia

Nuestro servicio puede ayudarte a controlar que no realices más de una transacción aprobada para un proceso único. Esto se hace identificando ese proceso con un valor único que sería enviado en el parámetro `idempotenceKey`, este hará que no se procese de nuevo una transacción si ya hay una pendiente o aprobada con el mismo valor.

```
{
    ...
    "idempotenceKey": "ABCD1234",
    "instrument": {
    ...
}
```

## Flujo básico

Se hace la primera transacción con un idempotenceKey y la respuesta será por ejemplo una aprobación, o una pendiente.

![IdempotenceFirst.png](../assets/images/IdempotenceFirst.png)

Si se solicita nuevamente la transacción con el mismo valor, se retornará exactamente lo mismo de la primera vez pero con un HTTP Code 208 en vez de un 200

![IdempotenceSecond.png](../assets/images/IdempotenceSecond.png)


## Observaciones

El parametro se encuentra en la raiz de la petición de autorización y es un alfanumérico de 32.

Es el único valor que afecta este comportamiento, es decir, la referencia, el monto y el instrumento puede variar y aún así, si el idempotenceKey es el mismo, no se hará una nueva transacción