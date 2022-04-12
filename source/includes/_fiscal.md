# Fiscal
Métodos para la obtención de documentos de carácter fiscal.

## Obtener modelos fiscales
Obtención de los modelos fiscales.

```shell

# El servicio 'contract/employee/workplace' es una llamada GET
curl --request GET "https://aon.solutions/ms/api/fiscal/models"
 -H "session_id:YOURSESSIONID" --data
 -H "domain_name:NOMBRE_DEL_DOMINIO" --data
```

> Ejemplo de JSON de respuesta:

```json
[
    {
        "period": "T4",
        "year": 2021,
        "administration": "COMMON_TERRITORY",
        "surname": "RAYSON CORPORATION",
        "domain": 7138,
        "document": "B12345678",
        "name": "RAYSON CORPORATION",
        "model": "IVA",
        "id": 19337,
        "complementary": false,
        "replacement": false,
        "status": "FINISHED"
    },
    {
        "period": "T3",
        "year": 2021,
        "administration": "COMMON_TERRITORY",
        "surname": "RAYSON CORPORATION",
        "domain": 7138,
        "document": "B12345678",
        "name": "RAYSON CORPORATION",
        "model": "IVA",
        "id": 13452,
        "complementary": false,
        "replacement": false,
        "status": "FINISHED"
    },
    {
        "period": "T2",
        "year": 2021,
        "administration": "COMMON_TERRITORY",
        "surname": "RAYSON CORPORATION",
        "domain": 7138,
        "document": "B12345678",
        "name": "RAYSON CORPORATION",
        "model": "IVA",
        "id": 9937,
        "complementary": false,
        "replacement": false,
        "status": "FINISHED"
    },
    {
        "period": "T1",
        "year": 2021,
        "administration": "COMMON_TERRITORY",
        "surname": "RAYSON CORPORATION",
        "domain": 7138,
        "document": "B12345678",
        "name": "RAYSON CORPORATION",
        "model": "IVA",
        "id": 6829,
        "complementary": false,
        "replacement": false,
        "status": "FINISHED"
    }
]
```

### HTTP Request

`GET https://aon.solutions/ms/api/fiscal/models`

### Parámetros

No requiere

### Respuesta

| Name |  Type  | Description |
|------|--------|-------------|
| period            | string    | Período                          |
| year              | number    | Año                              |
| administration    | string    | Administración                   |
| surname           | string    | Apellido                         |
| domain            | number    | Identificador del dominio        |
| document          | string    | NIF                              |
| name              | string    | Nombre                           |
| model             | string    | Modelo                           |
| id                | number    | Identificador del modelo         |
| complementary     | boolean   | Complementario                   |
| replacement       | boolean   | Reemplazo                        |
| status            | string    | Estado                           |