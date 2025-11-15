README.md – FoodDeliverySystem_MVC (Java CLI Project)

A Java console-based Food Delivery System implemented using a clean MVC structure:

Admin side (manage restaurants, food items, orders, statuses)

User side (register, login, browse restaurants, view menu, place orders, view order status)

Controllers → Services → DAOs → Models separation

In-memory CRUD storage (replaceable with JDBC/DB later)

This README includes:

Full setup steps

Compilation & run guide

Admin user manual

Customer user manual

Folder structure

Troubleshooting

🚀 1. Project Structure
src/
  com/fooddelivery/
      Main.java
      controller/
          AuthController.java
          AdminController.java
          UserController.java
      service/
          AuthService.java
          AdminService.java
          UserService.java
      dao/
          UserDAO.java
          RestaurantDAO.java
          FoodItemDAO.java
          OrderDAO.java
      model/
          User.java
          Admin.java
          Customer.java
          Restaurant.java
          FoodItem.java
          Order.java

⚙️ 2. Prerequisites

Install Java JDK 17+
Check versions:

java -version
javac -version


Both must return a version number.

🛠 3. How to Compile and Run
Step 1: Navigate to project folder
cd FoodDeliverySystem_MVC

Step 2: Compile
Linux / macOS / Git Bash
javac -d out $(find src -name "*.java")

Windows PowerShell
Get-ChildItem -Recurse -Filter *.java | ForEach-Object { $_.FullName } | %{ javac -d out $_ }

Step 3: Run
java -cp out com.fooddelivery.Main


The Welcome screen appears.

🔐 4. Login Credentials
Admin (default)
username: admin
password: admin123

Customers

Created through the Register option in the main menu.

🧭 5. Main Menu (Entry Screen)
=== FOOD DELIVERY SYSTEM ===
1. Login
2. Register (Customer)
3. Exit

🛡 6. ADMIN GUIDE (Full Steps)

Login as admin → Admin Menu:

--- ADMIN MENU ---
1. Add Restaurant
2. Remove Restaurant
3. Add Food Item
4. Remove Food Item
5. View All Restaurants
6. View All Orders
7. Update Order Status
8. Back

✔ 1. Add Restaurant

Creates a new restaurant entry.
Inputs: restaurant ID, restaurant name.

✔ 2. Remove Restaurant

Deletes a restaurant by ID.

✔ 3. Add Food Item (Global Menu)

Creates a food item with:

food ID

food name

price

✔ 4. Remove Food Item

Deletes a food item from global pool.

✔ 5. View All Restaurants

Shows all restaurants + global food items.

✔ 6. View All Orders

Shows:

order id

customer name

item summary

total

status

✔ 7. Update Order Status

Updates order status to:

Placed

Accepted

Prepared

Out for Delivery

Delivered

✔ 8. Back

Returns to login screen.

Admin Example
Add Restaurant → (102, "QuickBites")
Add Food Item → (5, "Veg Sandwich", 80)
View All Restaurants
Update Order Status → (orderId = 1, status = Delivered)

👤 7. USER GUIDE (Full Steps)

Customers must register first, then login.

📍 User Menu
--- USER MENU ---
1. Browse Restaurants
2. Browse Restaurant Menu
3. Place Order
4. My Orders
5. Logout

✔ 1. Browse Restaurants

Shows available restaurants.

✔ 2. Browse Restaurant Menu

Enter restaurant ID → see food items.

✔ 3. Place Order

Flow:

Enter restaurant ID

Enter food ID + quantity repeatedly

Enter 0 to finish

Order stored with status Placed

✔ 4. My Orders

User sees:

order id

total price

current status

✔ 5. Logout

Returns to main menu.

🧪 8. Example User Walkthrough

Register:

username: karishma
password: pass123


Login

Browse restaurants

Place order from restaurant 101:

Food ID 1 qty 2

Food ID 2 qty 1

enter 0 to finish

View orders — status starts as Placed

Admin updates status to Delivered

🗂 9. Seeded Data (Default)
Restaurant (preloaded)
ID: 101
Name: HariOmDhaba
Menu:
   1: Pav Bhaji – 140
   2: Paneer Butter Masala – 220

🧱 10. Persistence Notes

Currently:

All DAOs use in-memory LinkedHashMap

Data disappears after program exits

To enable database storage:

Implement JDBC versions of DAOs

Use SQLite or MySQL

Ask me and I will generate a DB-backed project
