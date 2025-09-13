
#### Workflow of Single API

![[Pasted image 20250710093617.png]]

---
#### Annotations

**Spring Boot Annotations** are a form of metadata that provides data about a spring 
application. Spring Boot is built on the top of the spring and contains all the features of spring.

- It allows for avoiding heavy configuration of XML which is present in the spring
- It provides easy maintenance and creation of REST endpoints

---
#### Commonly Used Annotations
https://chatgpt.com/share/686f42b5-a158-8004-8731-3acbd4db06a5

---
#### Layers in Spring Boot

1. Controller
2. Service
3. Persistance (ORM -> Objects Relational Mapping)
4. DB Layer (JPA)

----

#### Workflow with all layers

1. We get the data from the controller we map the data using  RequestDTO
2. From the RequestDTO it hits the Controller Layer , in that data injection has been done
3. After controller layer the function that defined in the service Layer with perform 
4. From that the Data are passed to the JPA repository which is persistance layer which uses the ORM (Objects Relational Mapping)  
5. From the JPA repository the data is stored to the Database

___



