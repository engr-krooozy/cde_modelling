# cde_modelling

​​1. Entities, Relationships, and Constraints
Entities:
Location: Represents each outlet of the restaurant. Contains information about the physical location and variations in the menu.
Menu Items (can be derived from Transactions and Location): Includes information about each food item, such as category and pricing.
Sales Transactions: Represents the transactional details, such as time, location, customer, and payment method. It's a fact table that records sales.
Customer: Information about each customer for tracking behaviour and applying personalized promotions.
Payment Method (Derived from paymentType): Captures the method of payment for each transaction, such as cash, POS, or online.
Inventory (Can be inferred from the dining options and menu in locations): Tracks the stock levels of each menu item in different locations.
Relationships:
Location ↔ Sales Transactions: One-to-many relationship between locations and transactions. A location has many sales.
Menu Items ↔ Sales Transactions: Menu items are linked to sales transactions, representing what the customer ordered.
Sales Transactions ↔ Customers: Each sales transaction is linked to a customer, allowing personalized tracking.
Sales Transactions ↔ Payment Method: Each transaction must be associated with a valid payment method.
Inventory ↔ Location: Each menu item’s inventory level is tracked per location. After each sale, the stock is updated.
Constraints:
Every sales transaction must have a valid location and payment method.
Customers must have valid IDs for personalized tracking.
Inventory must be updated after each transaction to ensure no stockouts.
2. Creating the Dimensional Model
Business Process Chosen:
Sales Monitoring and Inventory Management: The primary goal is to track sales trends and effectively manage stock across different locations, accounting for customer preferences and demand patterns.
Business Questions:
What are the most popular menu items across different locations?
How do payment methods vary across locations?
Which location has the highest sales volume?
How can stock depletion be predicted to prevent shortages?
Grain:
The grain is the sales transaction level. Each record represents an individual sale.
Dimensions:
Date Dimension:
Tracks the time aspects of the transaction, including day, month, and year.
Location Dimension:
Captures details about each location, such as name and state.
Customer Dimension:
Includes customer details like name and state for tracking purchasing behaviours.
Payment Method Dimension:
Captures the method of payment for each sale, such as cash, POS, or online.
Menu Item Dimension (Inferred from transactions and location):
Contains details on each menu item, including name, category, and price.
Fact Table: Sales Transaction Table
Foreign Keys:
LocationID: Links to the location where the transaction took place.
CustomerID: Links to the customer making the purchase.
PaymentType: Stores the method of payment.
Menu (Item): Stores the items purchased in each transaction.
Measures:
Total Sales Amount: The total amount for each transaction.
Quantity Sold: The quantity of items sold in each transaction.
Discounts Applied: If any discount or promotion is applied.
Stock Levels: Tracks the stock levels of menu items after each sale.
