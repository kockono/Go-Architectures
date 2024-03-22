## Arquitecturas

- [DDD Domain-Driven Design (Clean Architecture)](#ddd-domain-driven-design-clean-architecture)
- [MVC Modelo-Vista-Controlador](#mvc-modelo-vista-controlador)
- [Hexagonal Architecture](#hexagonal-architecture)
- [Arquitectura de servicios](#arquitectura-de-servicios)
- [Arquitectura de capas](#arquitectura-de-capas)
- [Arquitectura de Componentes](#arquitectura-de-componentes)

### DDD Domain-Driven Design (Clean Architecture)
```go
.
├── cmd
│   └── myapp
│       └── main.go
├── internal
│   ├── config
│   │   └── config.go
│   ├── handler
│   │   └── handler.go
│   ├── model
│   │   └── model.go
│   ├── repository
│   │   └── repository.go
│   └── server
│       └── server.go
├── vendor
├── go.mod
└── go.sum
```

- **cmd**: Directorio que contiene la entrada principal del programa.
    - **myapp**: Directorio que representa la aplicación principal.
        - **main.go**: Archivo principal que inicia la aplicación.
- **internal**: Directorio que contiene código interno del proyecto que no debe ser accesible desde fuera del proyecto.
    - **config**: Paquete que maneja la configuración de la aplicación.
        - **config.go**: Archivo que contiene la estructura y la lógica relacionada con la configuración.
    - **handler**: Paquete que maneja las solicitudes HTTP y las respuestas.
        - **handler.go**: Archivo que contiene la lógica del controlador (handler) para las solicitudes HTTP.
    - **model**: Paquete que define los modelos de datos de la aplicación.
        - **model.go**: Archivo que contiene las estructuras de datos utilizadas en la aplicación.
    - **repository**: Paquete que maneja el acceso a la base de datos o almacenamiento de datos.
        - **repository.go**: Archivo que contiene la lógica de acceso a la base de datos o almacenamiento de datos.
    - **server**: Paquete que inicializa y configura el servidor HTTP.
        - **server.go**: Archivo que contiene la lógica de inicialización y configuración del servidor HTTP.
- **vendor**: Directorio que contiene las dependencias de terceros (si se usan Go Modules).
- **go.mod**: Archivo de definición de módulo Go.
- **go.sum**: Archivo que contiene el checksum de las dependencias.

### MVC Modelo-Vista-Controlador
```go
.
├── cmd
│   └── myapp
│       └── main.go
├── internal
│   ├── controllers
│   │   └── controller.go
│   ├── models
│   │   └── model.go
│   └── views
│       └── view.go
├── static
├── templates
│   └── index.html
└── go.mod
```

- **cmd**: Directorio que contiene la entrada principal del programa.
    - **myapp**: Directorio que representa la aplicación principal.
        - **main.go**: Archivo principal que inicia la aplicación.
- **internal**: Directorio que contiene el código interno del proyecto.
    - **controllers**: Directorio que contiene los controladores de la aplicación.
        - **controller.go**: Archivo que contiene la lógica del controlador MVC.
    - **models**: Directorio que contiene los modelos de datos de la aplicación.
        - **model.go**: Archivo que contiene las estructuras de datos utilizadas en la aplicación.
    - **views**: Directorio que contiene las vistas de la aplicación.
        - **view.go**: Archivo que contiene la lógica de presentación de la aplicación.
- **static**: Directorio que contiene archivos estáticos como CSS, JavaScript, imágenes, etc.
- **templates**: Directorio que contiene archivos de plantillas HTML utilizados por las vistas.
    - **index.html**: Archivo de plantilla HTML para la página principal de la aplicación.
- **go.mod**: Archivo de definición de módulo Go.

- Los controladores (`controllers`) contienen la lógica de control de la aplicación y manejan las solicitudes HTTP.
- Los modelos (`models`) contienen las estructuras de datos y la lógica de negocio de la aplicación.
- Las vistas (`views`) contienen la lógica de presentación de la aplicación y se encargan de renderizar los datos en HTML.
- Los archivos estáticos (`static`) contienen recursos estáticos como archivos CSS, JavaScript e imágenes.
- Las plantillas (`templates`) contienen archivos de plantillas HTML utilizados por las vistas para generar páginas HTML dinámicas.

### Hexagonal Architecture
```go
.
├── cmd
│   └── myapp
│       └── main.go
├── internal
│   ├── adapters
│   │   ├── database
│   │   │   └── mysql.go
│   │   └── http
│   │       └── webserver.go
│   ├── domain
│   │   ├── model.go
│   │   ├── repository.go
│   │   └── service.go
│   └── usecase
│       └── usecase.go
├── vendor
└── go.mod
```

- **cmd**: Directorio que contiene la entrada principal del programa.
    - **myapp**: Directorio que representa la aplicación principal.
        - **main.go**: Archivo principal que inicia la aplicación.
- **internal**: Directorio que contiene el código interno del proyecto.
    - **adapters**: Directorio que contiene adaptadores para interactuar con servicios externos.
        - **database**: Directorio que contiene adaptadores para interactuar con la base de datos.
            - **mysql.go**: Archivo que contiene la implementación de la interfaz de repositorio para MySQL.
        - **http**: Directorio que contiene adaptadores para interactuar con la capa HTTP.
            - **webserver.go**: Archivo que contiene la configuración y gestión del servidor HTTP.
    - **domain**: Directorio que contiene la lógica de dominio de la aplicación.
        - **model.go**: Archivo que define los modelos de dominio.
        - **repository.go**: Archivo que define la interfaz del repositorio.
        - **service.go**: Archivo que define la lógica de negocio principal de la aplicación.
    - **usecase**: Directorio que contiene casos de uso de la aplicación.
        - **usecase.go**: Archivo que implementa la lógica de los casos de uso de la aplicación.
- **vendor**: Directorio que contiene las dependencias de terceros (si se usan Go Modules).
- **go.mod**: Archivo de definición de módulo Go.
    

En esta estructura:
- Los adaptadores (`adapters`) se encargan de interactuar con servicios externos, como la base de datos y el servidor HTTP. Estos adaptadores implementan interfaces definidas en el paquete `domain`.
- El paquete `domain` contiene la lógica de dominio de la aplicación, incluyendo los modelos de dominio, las interfaces de repositorio y la lógica de negocio.
- El paquete `usecase` contiene la implementación de los casos de uso de la aplicación, que orquestan la lógica de dominio para llevar a cabo tareas específicas.
- El directorio `cmd` contiene la entrada principal del programa, donde se inicializa la aplicación y se configuran los adaptadores.


### Arquitectura de servicios
```go
.
├── service1
│   ├── cmd
│   │   └── service1
│   │       └── main.go
│   ├── internal
│   │   └── service1
│   │       ├── handler.go
│   │       └── service.go
│   ├── go.mod
│   └── go.sum
├── service2
│   ├── cmd
│   │   └── service2
│   │       └── main.go
│   ├── internal
│   │   └── service2
│   │       ├── handler.go
│   │       └── service.go
│   ├── go.mod
│   └── go.sum
├── service3
│   ├── cmd
│   │   └── service3
│   │       └── main.go
│   ├── internal
│   │   └── service3
│   │       ├── handler.go
│   │       └── service.go
│   ├── go.mod
│   └── go.sum
└── go.mod
```
La arquitectura de microservicios es un enfoque de diseño de software en el que una aplicación se compone de varios servicios independientes, cada uno de los cuales se ejecuta en su propio proceso y se comunica con los demás a través de comunicación ligera, como HTTP o gRPC. Cada servicio es responsable de una parte específica de la funcionalidad de la aplicación y puede ser desarrollado, desplegado y escalado de forma independiente.

- Cada servicio (por ejemplo, `service1`, `service2`, `service3`) tiene su propio directorio raíz.
- Dentro de cada servicio, el directorio `cmd` contiene el punto de entrada principal del servicio.
- El directorio `internal` contiene el código interno del servicio, incluyendo los controladores (`handler.go`) que manejan las solicitudes HTTP o gRPC, y la lógica de negocio del servicio (`service.go`).
- Cada servicio tiene su propio archivo `go.mod`, que especifica sus dependencias.

En esta arquitectura:

- Cada servicio es autónomo y puede ser desarrollado, probado y desplegado de forma independiente.
- Los servicios se comunican entre sí a través de una interfaz bien definida, como HTTP o gRPC, lo que facilita la interoperabilidad.
- Los servicios pueden ser escalados de forma independiente según las necesidades de la aplicación.
- La arquitectura de microservicios permite una mayor modularidad, flexibilidad y capacidad de mantenimiento en comparación con las aplicaciones monolíticas.

### Arquitectura de capas
```go
.
├── cmd
│   └── myapp
│       └── main.go
├── internal
│   ├── handlers
│   │   └── handler.go
│   ├── services
│   │   └── service.go
│   └── repositories
│       └── repository.go
├── vendor
└── go.mod
```
La arquitectura de capas es un enfoque donde las diferentes capas de la aplicación están claramente definidas y separadas por su responsabilidad. Las capas típicas incluyen la capa de presentación, la capa de lógica de negocio y la capa de acceso a datos. Cada capa tiene una interfaz bien definida que permite la comunicación con las capas adyacentes.

- **cmd**: Directorio que contiene la entrada principal del programa.
    - **myapp**: Directorio que representa la aplicación principal.
        - **main.go**: Archivo principal que inicia la aplicación.
- **internal**: Directorio que contiene el código interno del proyecto.
    - **handlers**: Directorio que contiene los controladores de la aplicación, que manejan las solicitudes HTTP y otros eventos de entrada.
        - **handler.go**: Archivo que contiene la lógica de los controladores.
    - **services**: Directorio que contiene la lógica de negocio de la aplicación.
        - **service.go**: Archivo que contiene la lógica de los servicios de la aplicación.
    - **repositories**: Directorio que contiene la lógica de acceso a datos de la aplicación.
        - **repository.go**: Archivo que contiene la lógica de los repositorios para interactuar con la base de datos u otros sistemas de almacenamiento.

### Arquitectura de Componentes
```go
.
├── components
│   ├── authentication
│   │   ├── auth.go
│   │   └── jwt.go
│   ├── logging
│   │   └── logger.go
│   └── storage
│       ├── storage.go
│       └── s3.go
├── cmd
│   └── myapp
│       └── main.go
└── go.mod
```
La arquitectura de componentes es un enfoque donde la aplicación se construye a partir de componentes reutilizables que encapsulan la funcionalidad y el comportamiento. Cada componente tiene una interfaz bien definida que especifica cómo interactuar con él, lo que permite la composición y la reutilización de componentes en diferentes partes de la aplicación.

**components**: Directorio que contiene los componentes reutilizables de la aplicación.
- **authentication**: Directorio que contiene componentes relacionados con la autenticación de usuarios.
    - **auth.go**: Archivo que contiene la lógica de autenticación.
    - **jwt.go**: Archivo que contiene la lógica relacionada con JSON Web Tokens (JWT).
- **logging**: Directorio que contiene componentes relacionados con el registro y la auditoría.
    - **logger.go**: Archivo que contiene la lógica de registro de eventos.
- **storage**: Directorio que contiene componentes relacionados con el almacenamiento de datos.
    - **storage.go**: Archivo que define la interfaz de almacenamiento.
    - **s3.go**: Archivo que contiene la implementación para almacenamiento en Amazon S3.
