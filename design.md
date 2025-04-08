# Project Design Document

## Introduction

The Pizzeria API serves as a modern, centralized platform to help customers and pizzeria staff efficiently manage pizza orders. It offers RESTful endpoints that handle data related to toppings, pizza sizes, orders, and beverages, enabling users to seamlessly view, create, update, and remove resources related to a pizzeria’s operations.

## Background/Context

In the digital age, customers expect quick and convenient ways to order and customize their food, while pizzeria owners and staff need streamlined tools to manage their product offerings. The Pizzeria API aims to address these needs by providing a structured system where pizza-related resources can be accessed and manipulated. From managing available toppings and beverages to handling orders and different pizza sizes, this API empowers both end-users and the restaurant staff to maintain up-to-date information with minimal overhead.

## Stakeholders

- **Customers**: Individuals who use the application or website powered by this API to place pizza orders. They expect a user-friendly interface for selecting pizza sizes, toppings, and beverages, along with reliable updates on order status.

- **Pizzeria Staff/Management**: Responsible for adding, updating, and removing menu items such as toppings, pizza sizes, or beverages. They also need to manage orders efficiently to fulfill customer requests. The API’s reliability and feature set directly impact operational workflows.

## Functional Requirements

1. **Resource Creation**
   - The service shall allow pizzeria staff to create new resources (toppings, pizza sizes, orders, and beverages) via POST requests.
   - All incoming data shall be validated against predefined schemas before resource creation.
   - Upon successful creation, the service shall return a `201 Created` status code and the newly created resource in the response body.

2. **Resource Retrieval**
   - The service shall allow customers and staff to retrieve lists of toppings, pizza sizes, orders, and beverages via GET requests.
   - The service shall allow retrieval of a single resource by its unique identifier.
   - Upon successful retrieval, the service shall return a `200 OK` status code and the requested resource in the response body.

3. **Resource Update**
   - The service shall allow pizzeria staff to update existing resources (toppings, pizza sizes, orders, and beverages) via PUT requests.
   - All updated data shall be validated against predefined schemas.
   - Upon a successful update, the service shall return a `200 OK` status code and the updated resource in the response body.

4. **Resource Deletion**
   - The service shall enable pizzeria staff to delete existing resources (toppings, pizza sizes, orders, and beverages) via DELETE requests.
   - Upon successful deletion, the service shall return a `204 No Content` status code.
   - If an unauthorized user attempts to delete a resource, the service shall return a `403 Forbidden` status code.

5. **Data Validation**
   - The service shall validate data for all resource operations to ensure it meets the expected format and constraints.
   - If validation fails, the service shall return a `400 Bad Request` status code with details on the validation error.

6. **Authentication and Authorization**
   - The service shall require authentication for creating, updating, or deleting resources.
   - The service shall authorize users based on their roles, ensuring that only pizzeria staff can modify or remove resources.

7. **Error Handling**
   - The service shall provide clear error messages and proper HTTP status codes for all unsuccessful operations.
   - The service shall return `404 Not Found` if a requested resource is not found.
   - The service shall return `500 Internal Server Error` for unexpected server-side errors.

## Use Case Description

### Toppings
- **Create (POST)**
  - As pizzeria staff, I want to add new pizza toppings (e.g., pepperoni, mushrooms) so that customers can customize their pizzas with the latest options.
- **Read (GET)**
  - As a customer, I want to view all available toppings to personalize my pizza order.
  - As pizzeria staff, I need a complete list of toppings to ensure accurate inventory and menu updates.
- **Update (PUT)**
  - As pizzeria staff, I want to update topping information (e.g., name or availability) to reflect changes in our offerings.
- **Delete (DELETE)**
  - As pizzeria staff, I want to remove toppings that are no longer available or have been discontinued to maintain an accurate menu.

### PizzaSizes
- **Create (POST)**
  - As pizzeria staff, I want to add new pizza sizes (e.g., Small, Medium, Large) so that customers have different size options.
- **Read (GET)**
  - As a customer, I want to see all pizza sizes to choose the right one for my appetite.
  - As pizzeria staff, I need to retrieve size information to price pizzas correctly.
- **Update (PUT)**
  - As pizzeria staff, I want to update the attributes of a pizza size (e.g., diameter, price range) to keep the menu current.
- **Delete (DELETE)**
  - As pizzeria staff, I need to remove a pizza size that’s no longer offered to prevent confusion during the ordering process.

### Orders
- **Create (POST)**
  - As a customer, I want to place a new pizza order with specific toppings, size, and beverages.
- **Read (GET)**
  - As a customer, I want to view my existing orders to check on their status.
  - As pizzeria staff, I need a list of pending orders to process and fulfill them promptly.
- **Update (PUT)**
  - As pizzeria staff, I want to update the status of an order (e.g., from “Preparing” to “Out for Delivery”) or modify its details upon customer request.
- **Delete (DELETE)**
  - As pizzeria staff, I need to cancel or remove an order if requested by the customer or if it was placed in error.

### Beverages
- **Create (POST)**
  - As pizzeria staff, I want to add new beverage options (e.g., soda, juice) for customers to purchase alongside their pizzas.
- **Read (GET)**
  - As a customer, I want to see the available beverages to complement my meal.
  - As pizzeria staff, I want to track beverage inventory and update the menu accordingly.
- **Update (PUT)**
  - As pizzeria staff, I want to modify beverage information such as size options or availability to keep the menu current.
- **Delete (DELETE)**
  - As pizzeria staff, I want to remove beverages that are discontinued or out of stock to prevent incorrect orders.

## List Of Resources

- **Topping**: Represents an individual pizza topping (e.g., Pepperoni, Olives, Mushrooms).
- **PizzaSize**: Represents the available pizza sizes (e.g., Small, Medium, Large).
- **Order**: Represents a customer’s order, including chosen toppings, pizza size, beverages, and order status.
- **Beverage**: Represents the drinks available (e.g., Soda, Water, Juice).

## List of Endpoints

Below, `{id}` is replaced by a unique resource identifier (e.g., integer or string).

### Toppings
- **POST** `/api/toppings`
  - **Description**: Create a new topping.
  - **Request Body**:
    ```json
    {
      "id": "1",
      "name": "Pepperoni",
      "isVegetarian": false,
      "isVegan": false
    }
    ```
  - **Response**: `201 Created` with the created topping object.
  - **Error**: `400 Bad Request` if input validation fails.

- **GET** `/api/toppings`
  - **Description**: Retrieve a list of all toppings.
  - **Response**: `200 OK` with an array of topping objects.

- **GET** `/api/toppings/{id}`
  - **Description**: Retrieve details of a specific topping.
  - **Response**: `200 OK` with the topping object.
  - **Error**: `404 Not Found` if the topping does not exist.

- **PUT** `/api/toppings/{id}`
  - **Description**: Update an existing topping.
  - **Request Body**:
    ```json
    {
      "id": "1",
      "name": "Pepperoni",
      "isVegetarian": false,
      "isVegan": false
    }
    ```
  - **Response**: `200 OK` with the updated topping object.
  - **Error**: `400 Bad Request` if validation fails; `404 Not Found` if the topping does not exist.

- **DELETE** `/api/toppings/{id}`
  - **Description**: Delete a specific topping.
  - **Response**: `204 No Content`.
  - **Error**: `404 Not Found` if the topping does not exist; `403 Forbidden` if unauthorized.

### PizzaSizes
- **POST** `/api/pizzasizes`
  - **Description**: Create a new pizza size.
  - **Request Body**:
    ```json
    {
      "id": "1",
      "name": "Large",
      "diameterInInches": 16
    }
    ```
  - **Response**: `201 Created` with the created pizza size object.
  - **Error**: `400 Bad Request` if input validation fails.

- **GET** `/api/pizzasizes`
  - **Description**: Retrieve a list of all pizza sizes.
  - **Response**: `200 OK` with an array of pizza size objects.

- **GET** `/api/pizzasizes/{id}`
  - **Description**: Retrieve details of a specific pizza size.
  - **Response**: `200 OK` with the pizza size object.
  - **Error**: `404 Not Found` if the pizza size does not exist.

- **PUT** `/api/pizzasizes/{id}`
  - **Description**: Update an existing pizza size.
  - **Request Body**:
    ```json
    {
      "id": "1",
      "name": "Large",
      "diameterInInches": 16
    }
    ```
  - **Response**: `200 OK` with the updated pizza size object.
  - **Error**: `400 Bad Request` if validation fails; `404 Not Found` if the pizza size does not exist.

- **DELETE** `/api/pizzasizes/{id}`
  - **Description**: Delete a specific pizza size.
  - **Response**: `204 No Content`.
  - **Error**: `404 Not Found` if the pizza size does not exist; `403 Forbidden` if unauthorized.

### Orders
- **POST** `/api/orders`
  - **Description**: Create a new order.
  - **Request Body**:
    ```json
    {
      "id": "1001",
      "pizzaSize": { "id": "1" },
      "toppings": [
        { "id": "1" },
        { "id": "2" }
      ],
      "beverages": [
        { "id": "1" }
      ],
      "status": "Preparing"
    }
    ```
  - **Response**: `201 Created` with the created order object.
  - **Error**: `400 Bad Request` if input validation fails.

- **GET** `/api/orders`
  - **Description**: Retrieve a list of all orders.
  - **Response**: `200 OK` with an array of order objects.

- **GET** `/api/orders/{id}`
  - **Description**: Retrieve details of a specific order.
  - **Response**: `200 OK` with the order object.
  - **Error**: `404 Not Found` if the order does not exist.

- **PUT** `/api/orders/{id}`
  - **Description**: Update an existing order (e.g., change order status or modify toppings).
  - **Request Body**:
    ```json
    {
      "id": "1001",
      "pizzaSize": { "id": "1" },
      "toppings": [
        { "id": "1" },
        { "id": "2" }
      ],
      "beverages": [
        { "id": "1" }
      ],
      "status": "Out for Delivery"
    }
    ```
  - **Response**: `200 OK` with the updated order object.
  - **Error**: `400 Bad Request` if validation fails; `404 Not Found` if the order does not exist.

- **DELETE** `/api/orders/{id}`
  - **Description**: Cancel or remove an existing order.
  - **Response**: `204 No Content`.
  - **Error**: `404 Not Found` if the order does not exist; `403 Forbidden` if unauthorized.

### Beverages
- **POST** `/api/beverages`
  - **Description**: Create a new beverage option.
  - **Request Body**:
    ```json
    {
      "id": "1",
      "name": "Cola",
      "isCarbonated": true,
      "sizeOptions": ["Can", "Bottle"]
    }
    ```
  - **Response**: `201 Created` with the created beverage object.
  - **Error**: `400 Bad Request` if input validation fails.

- **GET** `/api/beverages`
  - **Description**: Retrieve a list of all beverages.
  - **Response**: `200 OK` with an array of beverage objects.

- **GET** `/api/beverages/{id}`
  - **Description**: Retrieve details of a specific beverage.
  - **Response**: `200 OK` with the beverage object.
  - **Error**: `404 Not Found` if the beverage does not exist.

- **PUT** `/api/beverages/{id}`
  - **Description**: Update an existing beverage.
  - **Request Body**:
    ```json
    {
      "id": "1",
      "name": "Cola",
      "isCarbonated": true,
      "sizeOptions": ["Can", "Bottle"]
    }
    ```
  - **Response**: `200 OK` with the updated beverage object.
  - **Error**: `400 Bad Request` if validation fails; `404 Not Found` if the beverage does not exist.

- **DELETE** `/api/beverages/{id}`
  - **Description**: Delete a specific beverage option.
  - **Response**: `204 No Content`.
  - **Error**: `404 Not Found` if the beverage does not exist; `403 Forbidden` if unauthorized.

## Error Handling Strategies
- **Validation Errors**: Return `400 Bad Request` with detailed error messages.
- **Authentication/Authorization Errors**: Return `401 Unauthorized` for authentication failures and `403 Forbidden` for access violations.
- **Not Found Errors**: Return `404 Not Found` when a requested resource is missing.
- **Server Errors**: Return `500 Internal Server Error` if the server encounters an unexpected condition.

## UML Diagrams

![Pizzeria UML Diagram](PizzeriaUML.png)

