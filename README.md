# Trading System
The trading system facilitates transactions between sellers and buyers through a platform consisting of various stores with product inventories. Users can take on roles as sellers, buyers, or administrators, managing stores, setting purchase and discount policies, and appointing additional managers. The system also integrates with external services for payment processing and product delivery, while providing real-time notifications and maintaining security and usability to protect user data and ensure a seamless user experience.

<h4>Link to draw.io</h4>https://app.diagrams.net/?src=about#G1u-V6VvQq7JaZmhXwCBrdD2hGcZ5PgKCl#%7B%22pageId%22%3A%22RSWp_Q7aErI8Epxvq06W%22%7D

<h4>Link to use-cases</h4>https://docs.google.com/document/d/1vNO6_xK7hVnTdWi6pEBej4DQUyK4Fje9h5tHBA-OYq4/edit?usp=sharing

# JSON Configuration File Creation Guide

This guide explains how to create a JSON configuration file for the `Configuration` class in your application. This file will be used to initialize various services and settings.

## JSON Configuration File Structure

The JSON configuration file must follow a specific structure to be correctly interpreted by the `Configuration` class. Below is a detailed breakdown of the required structure.

### Example JSON Configuration File

```json
{
  "payments service": {
    "DefaultPaymentGateway": {}
  },
  "supplier service": {
    "DefaultSupplySystem": {}
  },
  "Admin details": {
    "user": "admin",
    "password": "adminPassword"
  },
  "init sequence": [
    {
      "function": "register",
      "parameters": {
        "username": "mia",
        "password": "Password123!"
      }
    },
    {
      "function": "loginAsSubscriber",
      "parameters": {
        "username": "mia",
        "password": "Password123!"
      }
    },
    {
      "function": "addStore",
      "parameters": {
        "storeName": "newStore",
        "ownerUsername": "mia"
      }
    },
    {
      "function": "addProductToStore",
      "parameters": {
        "storeIndex": 0,
        "productName": "Example Product",
        "description": "An example product",
        "price": 9.99,
        "quantity": 100,
        "type": ["Category1", "Category2"],
        "ownerUsername": "mia"
      }
    }
  ]
}
```

### Detailed Structure

1. **Payments Service**

   This section specifies the payment gateway configuration. The configuration should include either a `DefaultPaymentGateway` or a `ProxyPaymentGateway`.

   ```json
   "payments service": {
     "DefaultPaymentGateway": {}
   }
   ```

   - `DefaultPaymentGateway`: Initializes the default payment gateway.
   - `ProxyPaymentGateway`: Initializes the proxy payment gateway.

2. **Supplier Service**

   This section specifies the supplier system configuration. The configuration should include either a `DefaultSupplySystem` or a `ProxySupplySystem`.

   ```json
   "supplier service": {
     "DefaultSupplySystem": {}
   }
   ```

   - `DefaultSupplySystem`: Initializes the default supply system.
   - `ProxySupplySystem`: Initializes the proxy supply system.

3. **Admin Details**

   This section provides the credentials for the admin user.

   ```json
   "Admin details": {
     "user": "admin",
     "password": "adminPassword"
   }
   ```

   - `user`: The username for the admin.
   - `password`: The password for the admin.

4. **Initialization Sequence**

   This section specifies the sequence of function calls to initialize the system. Each function call includes the function name and its parameters.

   ```json
   "init sequence": [
     {
       "function": "register",
       "parameters": {
         "username": "mia",
         "password": "Password123!"
       }
     },
     {
       "function": "loginAsSubscriber",
       "parameters": {
         "username": "mia",
         "password": "Password123!"
       }
     },
     {
       "function": "addStore",
       "parameters": {
         "storeName": "newStore",
         "ownerUsername": "mia"
       }
     },
     {
       "function": "addProductToStore",
       "parameters": {
         "storeIndex": 0,
         "productName": "Example Product",
         "description": "An example product",
         "price": 9.99,
         "quantity": 100,
         "type": ["Category1", "Category2"],
         "ownerUsername": "mia"
       }
     }
   ]
   ```

   - `function`: The name of the function to call.
   - `parameters`: A JSON object containing the parameters for the function.

### Supported Functions

Here are the supported functions and their required parameters:

- **register**
  - `username`: The username to register.
  - `password`: The password for the user.

- **loginAsSubscriber**
  - `username`: The username to log in as.
  - `password`: The password for the user.

- **addStore**
  - `storeName`: The name of the store.
  - `ownerUsername`: The username of the store owner.

- **addProductToStore**
  - `storeIndex`: The index of the store.
  - `productName`: The name of the product.
  - `description`: A description of the product.
  - `price`: The price of the product.
  - `quantity`: The quantity of the product.
  - `type`: An array of type for the product.
  - `ownerUsername`: The username of the store owner.

- **SendManagerNominationRequest**
  - `storeIndex`: The index of the store.
  - `ownerUsername`: The username of the store owner.
  - `managerUsername`: The username of the manager to nominate.
  - `permissions`: An array of permissions for the manager.

- **managerNominationResponse**
  - `requestId`: The ID of the nomination request.
  - `managerUsername`: The username of the manager.
  - `accepted`: Whether the nomination is accepted (true/false).

- **SendOwnerNominationRequest**
  - `storeIndex`: The index of the store.
  - `ownerUsername`: The username of the store owner.
  - `newOwnerUsername`: The username of the new owner.

- **ownerNominationResponse**
  - `requestId`: The ID of the nomination request.
  - `newOwnerUsername`: The username of the new owner.
  - `accepted`: Whether the nomination is accepted (true/false).

- **addProductToShoppingCart**
  - `storeIndex`: The index of the store.
  - `productId`: The ID of the product.
  - `quantity`: The quantity of the product.
  - `username`: The username of the subscriber.

- **logoutAsSubscriber**
  - `username`: The username of the subscriber to log out.

## Creating Your JSON Configuration File

1. Open a text editor or an IDE.
2. Create a new file and name it (e.g., `config.json`).
3. Copy the example JSON structure provided above into your file.
4. Modify the values according to your needs, ensuring that the structure is maintained.
5. Save the file.

Your JSON configuration file is now ready to be used with the `Configuration` class to initialize your application.
