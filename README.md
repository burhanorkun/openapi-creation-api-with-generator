# OpenApi 3.0 code generation

Api first creation with openapi yaml file
> /src/main/resources/api/openapi.yaml
```yaml
openapi: 3.0.3
info:
  title: Sample Ecommerce App
  description: ecommerce app API***
....
paths:
  /api/v1/carts/{customerId}:
    get:
      tags:
        - cart
      summary: Returns the shopping cart
      description: Returns the shopping cart of given customer
      operationId: getCartByCustomerId
      parameters:
        - name: customerId
          in: path
          description: Customer Identifier
          required: true
          schema:
            type: string
      responses:
        200:
          description: successful operation
```


Maven java resttemplate code generation
```xml
            <plugin>
                <groupId>io.swagger.codegen.v3</groupId>
                <artifactId>swagger-codegen-maven-plugin</artifactId>
                <version>3.0.32</version>
                <dependencies>
                    <dependency>
                        <groupId>com.github.jknack</groupId>
                        <artifactId>handlebars</artifactId>
                        <version>4.3.0</version>
                    </dependency>
                </dependencies>
                <executions>
                    <execution>
                        <goals>
                            <goal>generate</goal>
                        </goals>
                        <configuration>
                            <inputSpec>src/main/resources/api/openapi.yaml</inputSpec>
                            <language>spring</language>
                            <!--<language>java</language>-->
                            <!--<library>resttemplate</library>-->
                            <apiPackage>com.orkun.api.swagger2java</apiPackage>
                            <modelPackage>com.orkun.api.swagger2java.model</modelPackage>
                            <invokerPackage>com.orkun.api.swagger2java.handler</invokerPackage>
                            <configOptions>
                                <sourceFolder>src/main/java</sourceFolder>
                                <dateLibrary>java8</dateLibrary>
                            </configOptions>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
```

Run swagger plugin
> $ mvn clean package

if you want you can create server and client codes with swagger editor by openapi yaml
<br/>
[swagger editor](https://editor.swagger.io/)

---
Burhan Orkun