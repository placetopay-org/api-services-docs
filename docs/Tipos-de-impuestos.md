---
tags: [Crear sesión]
---

# Impuestos

Los tipos de impuestos son las diferentes clases de tributo que las personas están obligadas a pagar a alguna organización.

En este sentido, dependiendo de la actividad sobre la que recaiga, se le aplica un impuesto u otro. Presentan variación en la cuantía que el interesado debe abonar. Esto se basa en la normativa que presente cada sistema tributario. 

En WebCheckout Placetopay los impuestos son enviados en el objeto `amount`  usado la estrcutura `taxes` 

            "taxes": [
                {
                    "kind": "ice",
                    "amount": 6.84
                },
                {
                    "kind": "valueAddedTax",
                    "amount": 10.83
                }
            ],

El valor `kind` representa el tipo de impuesto que está incluido en el pago, los diferentes tipos de impuestos son:


Kind | País
---------|----------
 **valueAddedTax** | Todos
 **exciseDuty** | Todos
 **ice** | Todos
 **airportTax** | Colombia y Ecuador
 **stateTax** | Puerto Rico
 **MunicipalTax** | Puerto Rico 
**reducedStateTax** | Puerto Rico
 