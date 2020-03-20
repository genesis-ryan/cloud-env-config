# cloud-env-config

## micro service cloud config

1. add bootstrap file on micro service
bootstrap.yml

```
spring:
  application:
    name: partner-service
  cloud:
    consul:
      host: 127.0.0.1
      port: 8500
      config:
        enabled: true
        prefix: cloud-env-config/microservice/${spring.application.name}
        defaultContext: application
        format: FILES
        profileSeparator: ','
        watch:
          enabled: false
```

2. add config file on this git repo
the file dir and file name are constraint strictly.
ex: 

spring.application.name = partner-service

profile = dev

file dir: 
```
microservice/partner-service
```
file name:
```
partner-service-dev.yml
partner-service.yml
application-dev.yml
application.yml

partner-service-dev.properties
partner-service.properties
application-dev.properties
application.properties
```

3. add dependency on pom.xml

```
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-consul-config</artifactId>
</dependency>
```
