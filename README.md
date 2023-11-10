# Ecommerce-sql-project
This repository showcases an SQL project focused on e-commerce database management. It includes the creation of tables for products and sales, sample data insertion, and queries for viewing product inventory, analyzing sales, and gaining insights into customer behavior. Explore and learn SQL fundamentals with this practical e-commerce scenario.
'''
-- Create Products Table
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    Category VARCHAR(30),
    Price DECIMAL(10, 2),
    QuantityAvailable INT,
    SupplierID INT
);

-- Create Sales Table
CREATE TABLE Sales (
    SaleID INT PRIMARY KEY,
    ProductID INT,
    QuantitySold INT,
    SaleDate DATE,
    BuyerID INT
);

-- Insert Sample Products
INSERT INTO Products (ProductID, ProductName, Category, Price, QuantityAvailable, SupplierID)
VALUES (1, 'T-Shirt', 'Clothing', 19.99, 100, 101),
       (2, 'Mobile Phone', 'Electronics', 299.99, 50, 102),
       (3, 'Book', 'Education', 12.50, 75, 103);

-- Insert Sample Sales
INSERT INTO Sales (SaleID, ProductID, QuantitySold, SaleDate, BuyerID)
VALUES (1, 1, 5, '2023-10-01', 201),
       (2, 2, 2, '2023-10-05', 202),
       (3, 1, 3, '2023-10-10', 203);

-- Query: View Product Inventory
SELECT ProductID, ProductName, Category, Price, QuantityAvailable
FROM Products;

-- Query: Sales Analysis
SELECT ProductID, SUM(QuantitySold) AS TotalSold
FROM Sales
GROUP BY ProductID
ORDER BY TotalSold DESC;

-- Query: Customer Insights
SELECT BuyerID, COUNT(SaleID) AS TotalPurchases
FROM Sales
GROUP BY BuyerID
ORDER BY TotalPurchases DESC;
'''
