# Trivial API

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

## Consultar datos
```plain
GET: http://localhost:port/api/x/collectioname/level/format/filter/page/sort/tql
```

