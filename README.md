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
		client_id:		clientid
		client_secret:	testpass
```

```plain
curl -u client_id:client_secret http://localhost:port/api/x/token -d "grant_type=password&username=ANTONIO.RAMIREZ&password=314159"
```

## Recuperar instancias
```plain
GET: http://localhost:port/api/x/collectioname/id/level/format/filter/page/sort/tql/actions
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

## Trivial Validations - Transformations 

> El API Trivial Incluye un mecanismo básico de
validaciones de los tipos de datos en los modelos, que
consiste en sentencias en los comentarios de las propiedades, encerrados entre corchetes [] y en lineas separadas, las cuales se listan a continuación.

> Ejemplo:

```php
/**
* [@Required]
* [@Range(1-10)]
* [@Type(integer)]
* [@IdentifierOf(Grupo->Nombre = Nombre && Grupo->Undone=Undone )]
* [@TransformWith(UniqueRule)Mensaje de Cancelación si es Blanco]
* [@TransformWithReference(Main)Mensaje de Cancelación si es Blanco]
*/
public $edad;
```

### @Required

> Si esta presente debe contener un valor

### @Type(DATATYPE)

> Puede ser: 
* integer, long
* float  , double
* string
* datetime, date
* boolean , bool

### @StringLength(NUMBER)

> Si se trata de un string se evalua su longitud

### @UpperCase

>  Convierte el valor a Mayúsculas 

### @LowerCase

>  Convierte el valor a Minúsculas 

### @Range(START-END)

> Esecifica un valor inicial y final ,este debe combinado con @Type(DATATYPE)

### @List(ONE|TWO|TREE)

> Si el elemento esta contenido en los elementos de la lista

### @Authorized

> Si se desea evaluar una condicion para edición

### @IdentifierOf

> Si se desea obtener identificador de una Entidad dependiendo de el valor actual

### @TransformWith

> Si se desea remplazar el valor por el resultado de un metodo del servicio o modelo

### @TransformWithReference

> Si se desea remplazar el valor por el resultado de un metodo del servicio o modelo (se recibe la toda la instancia actual)

### @Ignored

> Se ignora el mapeo de este valor en la entidad

### @Protected

> Evita que la propiedad sea especifida en los elementos del datapack


### @Field

> Permite especificar el nombre del campo en la tabla asociado al la propiedad 

### @DisplayName

> Permite modificar el nombre de la propiedad en un mensaje de validacio	n 

### Notas

> Si se antepone el prefijo + a las propiedades anteriores la validaciones se efectua antes de persistir una instancia


