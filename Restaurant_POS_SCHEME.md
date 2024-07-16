# Restaurant Management System Database Schema

## Entities and Relationships

### Customer
```
+------------------+
| customer_id | Primary Key
| name |
| phone_number |
| email |
| address |
+------------------+
```

### Order
```
+------------------+
| order_id | Primary Key
| order_date |
| total_amount |
| status |
| customer_id | Foreign Key (Customer)
| table_id | Foreign Key (Table)
| user_id | Foreign Key (Sales User)
+------------------+
```

### Table
```
+------------------+
| table_id | Primary Key
| table_number |
| capacity |
| status |
+------------------+
```

### OrderItem
```
+------------------+
| order_item_id | Primary Key
| quantity |
| price |
| order_id | Foreign Key (Order)
| menu_item_id | Foreign Key (MenuItem)
+------------------+
```

### MenuItem
```
+------------------+
| menu_item_id | Primary Key
| name |
| description |
| price |
| category_id | Foreign Key (Category)
| is_available |
+------------------+
```

### Category
```
+------------------+
| category_id | Primary Key
| name |
| description |
+------------------+
```

### Takeaway
```
+------------------+
| takeaway_id | Primary Key
| order_id | Foreign Key (Order)
| pickup_time |
| delivery_person_id | Foreign Key (Delivery Person)
+------------------+
```
### Delivery Person
```
+------------------+
| delivery_person_id | Primary Key
| name |
| phone_number |
| vehicle_number |
+------------------+
```

### Kitchen
```
+------------------+
| kitchen_id | Primary Key
| name |
| location |
+------------------+
```
### Payment
```
+------------------+
| payment_id | Primary Key
| order_id | Foreign Key (Order)
| amount |
| payment_date |
| payment_method |
+------------------+
```
### Report 
```
+------------------+
| report_id | Primary Key
| report_date |
| report_type |
| details |
+------------------+
```
### Ingredient
```
+------------------+
| ingredient_id | Primary Key
| name |
| unit |
+------------------+
```
### Stock
```
+------------------+
| stock_id | Primary Key
| ingredient_id | Foreign Key (Ingredient)
| quantity |
+------------------+
```
### Reservation
```
+------------------+
| reservation_id | Primary Key
| customer_id | Foreign Key (Customer)
| reservation_time |
| table_id | Foreign Key (Table)
+------------------+
```
### Bar
```
+------------------+
| bar_id | Primary Key
| name |
| location |
+------------------+
```

## Relationships
- **Customer to Order:** One-to-Many (One customer can have multiple orders)
- **Order to Table:** Many-to-One (One order is associated with one table)
- **Order to OrderItem:** One-to-Many (One order can have multiple order items)
- **OrderItem to MenuItem:** Many-to-One (Each order item is associated with one menu item)
- **MenuItem to Category:** Many-to-One (Each menu item belongs to one category)
- **Takeaway to Order:** One-to-One (Each takeaway is associated with one order)
- **Kitchen to Order:** One-to-Many (One kitchen can handle multiple orders)
- **Bar to Order:** One-to-Many (One bar can handle multiple orders)
