[<- Regresar a la documentación]({{site.baseurl}}/)

<div id="step510"></div>
## 6.11. (Pago) Obtener un pago previamente realizado.

Este método permite obtener los detalles de un pago.

URL: `api/payment/find.json`

Método HTTP: `GET`

Parametros: `id`: Identificador del pago a consultar.

### Datos minimos a enviar

    {
        "id": "44a741ea-b8f1-11eb-924a-a3c0d8f958cb"
    }

### Ejemplo de Petición

    curl -X GET \
      'https://test.mpandco.com/api/payment/find.json?id=%idPayment%' \
      -H 'cache-control: no-cache' \
      -H 'authorization: Bearer OAUTH-TOKEN'

### Respuesta (Código 200)

    {
        "id": "44a741ea-b8f1-11eb-924a-a3c0d8f958cb",
        "created_at": "2021-05-19 18:26:34",
        "amount_environment_operation": "240.500000000000000000",
        "amount_total": "240.500000000000000000",
        "ref": "P2105193456333",
        "user": {
            "id": "401c5412-b8f1-11eb-924a-a3c0d8f958cb",
            "_data": {
                "fullname": "584125550000"
            }
        },
        "status": 4000,
        "payment_methods": [
            {
                "created_at": "2021-05-19 18:26:34",
                "operation_method": {
                    "id": "f126968b-0b2e-11e6-823a-5254007b4f9d",
                    "created_at": "2016-04-25 17:14:52",
                    "name": "mPandco a mPandco",
                    "description": "choice.payment_method.ve.balance.mpandco.description",
                    "icon": "mp-mpandco-mpandco",
                    "item_order": 1000,
                    "mode_operation": {
                        "id": "balance_mpandco",
                        "created_at": "2016-04-25 17:14:50",
                        "name": "Saldo mPandco"
                    },
                    "childs": [],
                    "mode_form": "SENDING",
                    "external_platform": "MPANDCO"
                },
                "amount_environment_operation": 240.5,
                "amount_total": 240.5,
                "item_operations": [
                    {
                        "created_at": "2021-05-19 18:26:34",
                        "description": "Monto a enviar",
                        "amount": 240.5
                    }
                ]
            }
        ],
        "type": 1000,
        "recipient": "584125550000",
        "digital_account_source": {
            "id": "41d17ff8-b8f1-11eb-924a-a3c0d8f958cb",
            "created_at": "2021-05-19 18:26:29",
            "name": "Camilo sexto"
        },
        "_data": {
            "summary_1": "Debitado: 240,50 VES",
            "summary_2": "240,50 VES",
            "summary_3": "Cuenta remitente",
            "summary_4": "Cuenta abonada",
            "summary_5": "Dinero enviado",
            "summary_status_color": "#FFA000",
            "username": "584122034949",
            "user_from": "584122034949",
            "amount": 0,
            "status": "Pendiente por recibir",
            "type_payment_label": "Env\u00edo de dinero a 584122034949",
            "summary_amount": {
                "summary_1": "240.500000000000000000",
                "summary_2": "240.500000000000000000"
            },
            "created_at": "hace menos de un minuto",
            "external_platform": "mPandco",
            "external_id": null
        }
    }

**Importante**: Debe verificar el estado del pago sea **"9000"** lo cual significa que fue realizado correctamente.

### Lista de estatus:
- (STATUS_CANCELED) **2000**: Cancelado (Cancelado por el usuario que lo emite, siempre y cuando el pago no sea recibido por el usuario receptor).
- (STATUS_APPROVED) **4000**: Aprobado (Aprobado por el sistema y esperando que el receptor acepte el pago).
- (STATUS_FINISH) **9000**: Completado correctamente.
