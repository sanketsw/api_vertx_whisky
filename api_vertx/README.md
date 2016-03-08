# Vert.x Example Maven Java Project

Example project for creating a Vert.x module with a Gradle build.

This module contains a simple Java verticle with one REST API

## How to run on bluemix
`cf push sanket_vertx -p target/api_vertx-0.0.1-SNAPSHOT-fat.jar -b java_buildpack`

Note the code in MyFirstVerticle to pick up the custom port of the cloud foundary app in bluemix
```
		int port = config().getInteger("http.port", 8080);
		String portProperty = System.getenv("VCAP_APP_PORT"); 
		if(portProperty!= null) {
			port = Integer.parseInt(portProperty);
			System.out.println("my cloud foundary Port is "+ port);
		}
```
Run API: http://sanket-vertx.mybluemix.net/api/whiskies
Run UI: http://sanket-vertx.mybluemix.net/assets/index.html

## How to run from eclipse

maven target `clean package`

run as Java Application - Main Class: `io.vertx.core.Starter` - 
Program arguments: `run com.ibm.api.api_vertx.MyFirstVerticle -conf src/main/conf/application.json`

Run API: http://localhost:8082/api/whiskies
Run UI: http://localhost:8082/assets/index.html
