# Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below. 


<ol type="a">
    <li> How many orders were shipped by Speedy Express in total? 
        <ol type="1">
            <li> QUERY:
                <br> SELECT COUNT(*) 
                <br> FROM Orders
                <br> WHERE ShipperID = 1;
            </li>
            <li> ANSWER:
                <br> 54 
            </li>
        </ol>
    </li>
    <li> What is the last name of the employee with the most orders? 
        <ol type="1">
            <li> QUERY:
                    SELECT Orders.EmployeeID, Employees.LastName, COUNT(*) AS FREQ
                    FROM Orders, Employees
                    WHERE Orders.EmployeeID=Employees.EmployeeID
                    GROUP BY Orders.EmployeeID, Employees.LastName
                    ORDER BY COUNT(*) DESC
            </li>
            <li> ANSWER:
                    Peacock
            </li>
        </ol>
    </li>
    <li> What product was ordered the most by customers in Germany?
        <ol type="1">
            <li> QUERY:
                    SELECT Products.ProductName, SUM(OrderDetails.Quantity) AS Total
                    FROM OrderDetails, Products
                    WHERE OrderDetails.ProductID=Products.ProductID AND OrderDetails.OrderID IN (
                        SELECT OrderID FROM Orders
                        WHERE CustomerID IN (
                            SELECT CustomerID FROM Customers
                            WHERE Country="Germany"
                        )
                    )
                    GROUP BY Products.ProductName
                    ORDER BY SUM(OrderDetails.Quantity) DESC
            </li>
            <li> ANSWER:
                    Boston Crab Meat
            </li>
        </ol>
    </li>            
</ol>
