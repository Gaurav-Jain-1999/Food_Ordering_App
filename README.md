# Burrito King Application
Overview
The Burrito King Application is a JavaFX-based GUI application that allows users to place orders for burritos, fries, and soda, manage their profiles, and view their order history. The application features functionalities for user registration, login, profile updates, order management, and payment processing.

## Techinical Specification
IDE Used: IntelliJ

Java Version: 22

JavaFX Version: 18.0.2

DataBase Used: SQLite

## UXML Diagram

```xml
<?xml version="1.0" encoding="UTF-8"?>
<UML>
    <Class name="CustomerController">
        <Field name="txtUsername" type="TextField"/>
        <Field name="txtPassword" type="PasswordField"/>
        <Field name="txtName" type="TextField"/>
        <Field name="txtSurname" type="TextField"/>
        <Field name="txtCard" type="TextField"/>
        <Method name="login" returnType="void"/>
        <Method name="register" returnType="void"/>
        <Method name="makeOrder" returnType="void"/>
        <Method name="viewOrders" returnType="void"/>
        <Method name="viewProfile" returnType="void"/>
        <Method name="logout" returnType="void"/>
        <Method name="navigateTo" returnType="void"/>
    </Class>
    <Class name="RegistrationController">
        <Field name="username" type="TextField"/>
        <Field name="password" type="TextField"/>
        <Field name="name" type="TextField"/>
        <Field name="surname" type="TextField"/>
        <Field name="mobile" type="TextField"/>
        <Field name="resultConsole" type="TextArea"/>
        <Method name="register" returnType="void"/>
        <Method name="return_back" returnType="void"/>
    </Class>
    <Class name="ProfileController">
        <Field name="username" type="TextField"/>
        <Field name="password" type="TextField"/>
        <Field name="name" type="TextField"/>
        <Field name="surname" type="TextField"/>
        <Field name="mobile" type="TextField"/>
        <Field name="resultConsole" type="TextArea"/>
        <Field name="cusId" type="int"/>
        <Method name="setCusId" returnType="void"/>
        <Method name="loadProfile" returnType="void"/>
        <Method name="updateProfile" returnType="void"/>
        <Method name="return_back" returnType="void"/>
    </Class>
    <Class name="Order">
        <Field name="orderId" type="int"/>
        <Field name="orderDetails" type="String"/>
        <Field name="orderTime" type="String"/>
        <Field name="orderStatus" type="String"/>
        <Method name="getOrderId" returnType="int"/>
        <Method name="getOrderDetails" returnType="String"/>
        <Method name="getOrderTime" returnType="String"/>
        <Method name="getOrderStatus" returnType="String"/>
    </Class>
    <Class name="OrdersController">
        <Field name="activeOrdersTable" type="TableView"/>
        <Field name="activeOrderDetailsColumn" type="TableColumn"/>
        <Field name="pastOrdersTable" type="TableView"/>
        <Field name="pastOrderDetailsColumn" type="TableColumn"/>
        <Field name="cancelOrderButton" type="Button"/>
        <Field name="collectOrderButton" type="Button"/>
        <Field name="cusId" type="int"/>
        <Method name="setCusId" returnType="void"/>
        <Method name="loadActiveOrders" returnType="void"/>
        <Method name="loadPastOrders" returnType="void"/>
        <Method name="initialize" returnType="void"/>
        <Method name="cancelOrder" returnType="void"/>
        <Method name="collectOrder" returnType="void"/>
    </Class>
    <Class name="Burrito">
        <Field name="batchPrepTime" type="int"/>
        <Field name="batchSize" type="int"/>
        <Method name="getPreparationTime" returnType="int"/>
        <Method name="getActualQuantityCooked" returnType="int"/>
    </Class>
    <Class name="Fries">
        <Field name="prepTimeForOneServe" type="int"/>
        <Field name="batchSize" type="int"/>
        <Method name="getPreparationTime" returnType="int"/>
        <Method name="getActualQuantityCooked" returnType="int"/>
    </Class>
    <Class name="Soda">
        <Field name="unitPrice" type="double"/>
        <Field name="quantity" type="int"/>
    </Class>
    <Class name="Restaurant">
        <Field name="name" type="String"/>
        <Field name="priceMap" type="HashMap<String, Double>"/>
        <Field name="remainedFries" type="int"/>
        <Field name="allOrders" type="LinkedList<Order>"/>
        <Method name="getPrice" returnType="double"/>
        <Method name="updatePrice" returnType="void"/>
        <Method name="updateRemainingServes" returnType="boolean"/>
        <Method name="addOrderToHistory" returnType="void"/>
    </Class>
    <Class name="NewOrderController">
        <Field name="burritoQuantity" type="TextField"/>
        <Field name="friesQuantity" type="TextField"/>
        <Field name="sodaQuantity" type="TextField"/>
        <Field name="cartTextArea" type="TextArea"/>
        <Field name="totalPriceTextField" type="TextField"/>
        <Field name="order" type="Order"/>
        <Field name="cusId" type="int"/>
        <Method name="addToCart" returnType="void"/>
        <Method name="updateCart" returnType="void"/>
        <Method name="placeOrder" returnType="void"/>
        <Method name="setCusId" returnType="void"/>
    </Class>
    <Class name="PaymentController">
        <Field name="cardNumberField" type="TextField"/>
        <Field name="expiryDateField" type="TextField"/>
        <Field name="cvvField" type="TextField"/>
        <Field name="orderTimeField" type="TextField"/>
        <Field name="resultConsole" type="TextArea"/>
        <Field name="order" type="Order"/>
        <Field name="cusId" type="int"/>
        <Method name="setCusId" returnType="void"/>
        <Method name="setOrder" returnType="void"/>
        <Method name="confirmPayment" returnType="void"/>
        <Method name="validateCard" returnType="boolean"/>
    </Class>
    <Class name="CSVExporter">
        <Method name="exportToCSV" returnType="void"/>
    </Class>
</UML>
```

## User Details - Example User

Username: johndoe

Password: password123

First Name: John

Last Name: Doe

Mobile: 1234567890

## How to Use

Registration: New users can register by providing their username, password, first name, last name, and mobile number.

Login: Registered users can log in using their username and password.

Profile Management: Users can update their profile details except for the username.

Order Management:

New Order: Users can place new orders by selecting the quantity of burritos, fries, and soda. They can update the cart and view the total price before placing the order.

Order History: Users can view their active and past orders. Active orders can be canceled or marked as collected.

Payment: When placing an order, users need to provide fake credit card information for payment validation. The system checks for a 16-digit card number, a future expiry date, and a 3-digit CVV.
