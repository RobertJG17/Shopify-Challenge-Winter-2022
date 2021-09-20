# Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below. 


<ol type="a">
    <li> How many orders were shipped by Speedy Express in total? 
        <ol type="1">
            <li> QUERY:
                <br> &nbsp;&nbsp;&nbsp;&nbsp; SELECT COUNT(*) 
                <br> &nbsp;&nbsp;&nbsp;&nbsp; FROM Orders
                <br> &nbsp;&nbsp;&nbsp;&nbsp; WHERE ShipperID = 1;
            </li>
            <li> ANSWER:
                <br> &nbsp;&nbsp;&nbsp;&nbsp; 54 
            </li>
        </ol>
    </li>
    <li> What is the last name of the employee with the most orders? 
        <ol type="1">
            <li> QUERY:
                <br> &nbsp;&nbsp;&nbsp;&nbsp; SELECT Orders.EmployeeID, Employees.LastName, COUNT(*) AS FREQ
                <br> &nbsp;&nbsp;&nbsp;&nbsp; FROM Orders, Employees
                <br> &nbsp;&nbsp;&nbsp;&nbsp; WHERE Orders.EmployeeID=Employees.EmployeeID
                <br> &nbsp;&nbsp;&nbsp;&nbsp; GROUP BY Orders.EmployeeID, Employees.LastName
                <br> &nbsp;&nbsp;&nbsp;&nbsp; ORDER BY COUNT(*) DESC
            </li>
            <li> ANSWER:
                    Peacock
            </li>
        </ol>
    </li>
    <li> What product was ordered the most by customers in Germany?
        <ol type="1">
            <li> QUERY:
                <br> &nbsp;&nbsp;&nbsp;&nbsp; SELECT Products.ProductName, SUM(OrderDetails.Quantity) AS Total
                <br> &nbsp;&nbsp;&nbsp;&nbsp; FROM OrderDetails, Products
                <br> &nbsp;&nbsp;&nbsp;&nbsp; WHERE OrderDetails.ProductID=Products.ProductID AND OrderDetails.OrderID IN (
                <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SELECT OrderID FROM Orders
                <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WHERE CustomerID IN (
                <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SELECT CustomerID FROM Customers
                <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WHERE Country="Germany"
                <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; )
                <br> &nbsp;&nbsp;&nbsp;&nbsp; )
                <br> &nbsp;&nbsp;&nbsp;&nbsp; GROUP BY Products.ProductName
                <br> &nbsp;&nbsp;&nbsp;&nbsp; ORDER BY SUM(OrderDetails.Quantity) DESC
            </li>
            <li> ANSWER:
                    Boston Crab Meat
            </li>
        </ol>
    </li>            
</ol>
