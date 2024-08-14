
# My Reply Assessment - Spring Boot Application

### Author - Charles Reilly

## Prerequisites

- Java JDK 22 - Java Development Kit
- Maven 3.8+ - Maven Build Tool

## Installation

1. Download the zip file provided.
2. Unzip the file provided.
3. Navigate to the project directory:
Important Note: For easier copy and pasting of commands. Please use the github readme linked here: 



   ```bash
   cd reply-technical-assessment/assessment/
   ```
4. Build the application:

   ```bash
   mvn clean install
   ```

## Execution

1. Run the application:

   ```bash
   java -jar target/reply-technical-assessment.jar
   ```
   The application will start on http://localhost:8080 by default.

## API Endpoints

### User Management

Note: Edge cases can be tested by altering these templates. For example, change parts of the request body to violate the 'basic validation checks'; as defined in the task description.

1. POST /users - Create a new user

   ```bash
   curl -X POST http://localhost:8080/users \
   -H "Content-Type: application/json" \
   -d '{
     "username": "charlesReilly",
     "password": "Password123",
     "emailAddress": "charles.reilly@example.com",
     "dob": "2000-01-01"
   }'
   ```

1. POST /users - Create a new user (With Credit Card)

   ```bash
   curl -X POST http://localhost:8080/users \
   -H "Content-Type: application/json" \
   -d '{
     "username": "charlesReilly2",
     "password": "Password123",
     "emailAddress": "charles.reilly@example.com",
     "dob": "2000-01-01",
     "cardNumber": "1234567812345678"
   }'
   ```

2. POST /users - Create a new user (Invalid, Underage)

   ```bash
   curl -X POST http://localhost:8080/users \
   -H "Content-Type: application/json" \
   -d '{
     "username": "youngUser",
     "password": "Password123",
     "emailAddress": "young.user@example.com",
     "dob": "2010-01-01"
   }'
   ```

3. POST /users - Create a new user (User Already Exists)

   ```bash
   curl -X POST http://localhost:8080/users \
   -H "Content-Type: application/json" \
   -d '{
     "username": "charlesReilly",
     "password": "Password123",
     "emailAddress": "charles.reilly@example.com",
     "dob": "2000-01-01"
   }'
   ```

4. GET /users - Retrieve all users

   ```bash
   curl -X GET http://localhost:8080/users
   ```

5. GET /users?CreditCard=Yes - Retrieve users with credit card filter (Yes)

   ```bash
   curl -X GET "http://localhost:8080/users?CreditCard=Yes"
   ```
6. GET /users?CreditCard=No - Retrieve users with credit card filter (No)

   ```bash
   curl -X GET "http://localhost:8080/users?CreditCard=No"
   ```
### Payment Processing

1. POST /payments - Process a payment

   ```bash
   curl -X POST http://localhost:8080/payments \
   -H "Content-Type: application/json" \
   -d '{
     "cardNumber": "1234567812345678",
     "amount": "100"
   }'
   ```

2. POST /payments - Process a payment (Invalid Credit Card Number)

   ```bash
   curl -X POST http://localhost:8080/payments \
   -H "Content-Type: application/json" \
   -d '{
     "cardNumber": "1234abcd5678efgh",
     "amount": "100"
   }'
   ```

3. POST /payments - Process a payment (Invalid Amount)

   ```bash
   curl -X POST http://localhost:8080/payments \
   -H "Content-Type: application/json" \
   -d '{
     "cardNumber": "1234567812345678",
     "amount": "-10"
   }'
   ```

4. POST /payments - Process a payment (Credit Card Not Registered)

   ```bash
   curl -X POST http://localhost:8080/payments \
   -H "Content-Type: application/json" \
   -d '{
     "cardNumber": "8765432187654321",
     "amount": "100"
   }'
   ```

## Packaging the Application

### Building a JAR File

To package the application as a JAR file, use the following command:

   ```bash
   mvn clean package
   ```
This will create a JAR file in the target directory. The JAR file can be run using:

   ```bash
   java -jar target/reply-technical-assessment.jar
   ```
