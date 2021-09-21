# Question 2: For this question you’ll need to use SQL. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below. 


<ol type="a">
    <li> How many orders were shipped by Speedy Express in total?
        <ol type="1">
            <br><li> QUERY:
                <br> &nbsp;&nbsp;&nbsp;&nbsp; SELECT COUNT(*) 
                <br> &nbsp;&nbsp;&nbsp;&nbsp; FROM Orders
                <br> &nbsp;&nbsp;&nbsp;&nbsp; WHERE ShipperID = 1;
            </li>
            <br>
            <li> ANSWER:
                <br> &nbsp;&nbsp;&nbsp;&nbsp; Speedy Express shipped 54 orders in total.
            </li>
        </ol>
    </li>
    <br>
    <li> What is the last name of the employee with the most orders?
        <ol type="1">
            <br><li> QUERY:
                <br> &nbsp;&nbsp;&nbsp;&nbsp; SELECT Orders.EmployeeID, Employees.LastName, COUNT(*) AS FREQ
                <br> &nbsp;&nbsp;&nbsp;&nbsp; FROM Orders, Employees
                <br> &nbsp;&nbsp;&nbsp;&nbsp; WHERE Orders.EmployeeID=Employees.EmployeeID
                <br> &nbsp;&nbsp;&nbsp;&nbsp; GROUP BY Orders.EmployeeID, Employees.LastName
                <br> &nbsp;&nbsp;&nbsp;&nbsp; ORDER BY COUNT(*) DESC
            </li>
            <br>
            <li> ANSWER:
                <br> &nbsp;&nbsp;&nbsp;&nbsp; Peacock is the last name of the employee with the most orders (40).
            </li>
        </ol>
    </li>
    <br>
    <li> What product was ordered the most by customers in Germany?
        <ol type="1">
            <br><li> QUERY:
                <br> &nbsp;&nbsp;&nbsp;&nbsp; SELECT Products.ProductName, SUM(OrderDetails.Quantity) AS Total
                <br> &nbsp;&nbsp;&nbsp;&nbsp; FROM OrderDetails, Products
                <br> &nbsp;&nbsp;&nbsp;&nbsp; WHERE OrderDetails.ProductID=Products.ProductID AND OrderDetails.OrderID IN (
                <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SELECT OrderID FROM Orders
                <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WHERE CustomerID IN (
                <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SELECT CustomerID FROM Customers
                <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WHERE Country="Germany"
                <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; )
                <br> &nbsp;&nbsp;&nbsp;&nbsp; )
                <br> &nbsp;&nbsp;&nbsp;&nbsp; GROUP BY Products.ProductName
                <br> &nbsp;&nbsp;&nbsp;&nbsp; ORDER BY SUM(OrderDetails.Quantity) DESC
            </li>
            <br>
            <li> ANSWER:
                <br> &nbsp;&nbsp;&nbsp;&nbsp; Boston Crab Meat was the most ordered product by German patrons (160).
            </li>
        </ol>
    </li>            
</ol>
