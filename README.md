# ServiceAdminServer
my try to create service admin server

I have tried to follow this [guide](https://www.baeldung.com/spring-boot-admin) to create service admin server, and with my client to register to it. howver, it takes me much time because of some version mismatch.

The initial page is applicaiton page, which for me a little misleading. when you click into the application, you may see some error other than info you expect. Wallboard in the correct one.

and for the security part, inside class WebSecurityConfig, the current ignoreMatchers can't be recognized. after change it to 
```
.ignoringAntMatchers("/applications","/applications/*","/instances","/instances/*","/actuator/**")

```
it works.

and also, in the application you want to regsiter, 
the properties in application.properties should be like

```
logging.level.de.codecentric.boot.admin.client=DEBUG
spring.boot.admin.client.url=http://localhost:8080
spring.boot.admin.client.username=user
spring.boot.admin.client.password=password
```
It is tricky that here spring.boot.admin.client means server side. I understand that from the application's point of view, it may be reasonable to name the admin server side as client side.

Client or server is a little misleading for me here. could we have better naming?

