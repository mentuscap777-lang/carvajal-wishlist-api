# Carvajal Wishlist API

API REST para gestionar lista de deseos de productos Carvajal E-commerce.

## 📋 Requisitos Funcionales Implementados

✅ Catálogo de productos con stock
✅ Agregar/eliminar productos de lista de deseos
✅ Listar deseos por usuario
✅ Histórico de cambios

## 🛠️ Stack

- Spring Boot 3.5.14
- Java 21
- MySQL 8.0
- JPA/Hibernate

## 📦 Base de Datos

```sql
CREATE DATABASE carvajal_wishlist;

CREATE TABLE productos (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100),
    precio DECIMAL(10,2),
    stock INT,
    descripcion VARCHAR(255)
);

CREATE TABLE lista_deseos (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    usuario_id BIGINT,
    producto_id BIGINT,
    fecha_agregado TIMESTAMP,
    FOREIGN KEY (producto_id) REFERENCES productos(id)
);

CREATE TABLE historico (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    usuario_id BIGINT,
    producto_id BIGINT,
    accion VARCHAR(50),
    fecha TIMESTAMP,
    FOREIGN KEY (producto_id) REFERENCES productos(id)
);

INSERT INTO productos VALUES
(NULL, 'Laptop Dell', 1200, 5, 'Laptop Intel i7'),
(NULL, 'Mouse Logitech', 25, 50, 'Mouse inalámbrico'),
(NULL, 'Teclado RGB', 75, 30, 'Teclado mecánico');
```

## 🚀 Ejecutar

```bash
git clone https://github.com/TU_USER/carvajal-wishlist-api.git
cd carvajal-wishlist-api
mvn clean install
mvn spring-boot:run
```

## 🔌 Endpoints

- `GET /api/productos` → Catálogo
- `GET /api/lista-deseos/{usuarioId}` → Mi lista
- `POST /api/lista-deseos` → Agregar
- `DELETE /api/lista-deseos/{id}` → Eliminar

## 📝 Configuración

`src/main/resources/application.yaml`:
```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/carvajal_wishlist
    username: root
    password: 123456
  jpa:
    hibernate:
      ddl-auto: update

server:
  port: 8080
```

## 👤 Autor

Sebastian Castro - SENA ADSO (Ficha 3292107)

## 📄 Próximas Mejoras

- Frontend Angular
- Tests unitarios
- Docker
- JWT Authentication
- Microservicios
