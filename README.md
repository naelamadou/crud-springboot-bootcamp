"# crud-springboot-bootcamp"
This project demonstrates how to create a CRUD (Create, Read, Update, Delete) application using Spring Boot, MySQL, and Spring Data JPA with a `Person` entity.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Postman Collection](#postman-collection)
- [Technologies Used](#technologies-used)

## Prerequisites

Before you begin, ensure you have the following installed on your machine:

- Java 8 or higher
- Maven
- MySQL
- Postman (optional, for API testing)

## Setup

1. **Clone the repository:**

    ```sh
    git clone https://github.com/naelamadou/crud-springboot-bootcamp
    cd crud-springboot-bootcamp
    ```

2. **Create a MySQL database:**

    ```sql
    CREATE DATABASE crud_springboot_bootcamp;
    ```

3. **Configure the database connection:**

   Open `src/main/resources/application.properties` and configure the following properties with your MySQL credentials:

    ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/crud-springboot
   spring.datasource.username=<your_user>
   spring.datasource.password=<your_user_password>
   spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.show-sql=true
   spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect
    ```

4. **Install dependencies and build the project:**

    ```sh
    mvn clean install
    ```
5**Explications des configurations DockerColpose:**
 :
version: '3.8': La version de la syntaxe Docker Compose.
services: La section où vous définissez les différents conteneurs qui composent votre application.
db: Le nom du service.
image: mysql:8.0: Spécifie l'image Docker à utiliser, ici MySQL version 8.0.
container_name: mysql-db: Le nom du conteneur.
environment: Les variables d'environnement pour configurer la base de données.
    MYSQL_ROOT_PASSWORD: Le mot de passe pour l'utilisateur root.
    MYSQL_DATABASE: Le nom de la base de données à créer au démarrage.
    MYSQL_USER: Le nom de l'utilisateur non-root.
    MYSQL_PASSWORD: Le mot de passe de l'utilisateur non-root.
    ports: La redirection des ports (externe
).
"3306:3306": Le port 3306 de l'hôte est redirigé vers le port 3306 du conteneur.
volumes: Les volumes Docker pour persister les données de la base de données.
db_data:/var/lib/mysql: Monte le volume db_data sur le répertoire /var/lib/mysql du conteneur.
volumes: Définition des volumes Docker.
db_data: Un volume nommé db_data qui est utilisé pour persister les données de la base de données.

## Running the Application


1. **Run the Spring Boot application:**

    ```sh
    ./mvnw spring-boot:run
    ```

2. The application will start and run on `http://localhost:8080`.

## API Endpoints

The following endpoints are available for the CRUD operations on the `Person` entity:

- **GET /api/persons**
    - Retrieve a list of all persons.

- **GET /api/persons/{id}**
    - Retrieve a single person by ID.

- **POST /api/persons**
    - Create a new person.
    - Example request body:
      ```json
      {
          "name": "John Doe",
          "city": "Los Angeles",
          "phoneNumber" : "999-777-444"
      }
      ```

- **PUT /api/persons/{id}**
    - Update an existing person by ID.
    - Example request body:
      ```json
      {
          "city": "New York",
          "phoneNumber" : "999-777-444"
      }
      ```

- **DELETE /api/persons/{id}**
    - Delete a person by ID.

## Postman Collection

A Postman collection to test each endpoint is included at the root of the project folder. You can import this collection into Postman to quickly test the API.

## Technologies Used

- **Spring Boot:** A framework to simplify the bootstrapping and development of new Spring applications.
- **Spring Data JPA:** A part of the larger Spring Data family to easily implement JPA-based repositories.
- **MySQL:** A relational database management system.
- **Maven:** A build automation tool used primarily for Java projects.
- **Lombok DEVELOPER TOOLS :** Java annotation library which helps to reduce boilerplate code.
## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or suggestions.


---

Happy coding!