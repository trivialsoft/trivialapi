# Trivial API
> Por Antonio Ramírez Santander

## Estructura
```plain
    App  - Api
				- Context.php
				- Controller.php
				- security.php
	     - Components
				- ComponentName.php
				- ComponentNameService.php
		 - Core
		        - Api.php
				- ExplicitColumns.php
				- Factory.php
				- Masso.php
				- Model.php
				- Parameters.php
				- Request.php 
				- TQL.php
				- TrivialAuthorizer.php
		 - Loop
				- Context.php
```	

## Autenticacion
```plain
      http://localhost:port/api/x/token
	  Headers:
	    Content-Type:	application/x-www-form-urlencoded
		Accept: 		application/json
	  Body:
		grant_type:		password
		username:		ANTONIO.RAMIREZ
		password:		314159
		client_id:		cleintid
		client_secret:	testpass
```

## Recuperar instancias
```plain
GET: http://localhost:port/api/x/collectioname/level/format/filter/page/sort/tql
```

## Persistir instancias
```plain
POST: http://localhost:port/api/x/any_collectioname

headers:
Content-Type:	application/json	
Authorization: 	Bearer 1234abc
body(raw+JSON(application/json)):
```

## Body 
```json
[
	{"modelname":"Ciudad",
	"Ciudad":1,
	"Nombre":"Monterrey"
	},
	{"modelname":"Ciudad",
	"Ciudad":2,
	"Nombre":"Tuxpan"
	}
]
```

## Respuesta de confirmación
```json
{
    "resp": "Actualizado",
    "id": "2",
    "model": "Ciudad",
    "status": 1,
    "updates": "{'Ciudad_1':'1','Ciudad_2':'2'}",
    "exmessage": ""
}
```


