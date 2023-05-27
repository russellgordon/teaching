---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/solutions/databases/","dgHomeLink":false}
---

# Databases

## Exercise Solutions

1.  Find a list of all the departments in the company.  
   ![Pasted image 20230329194442.png](/img/user/Attachments/Pasted%20image%2020230329194442.png)
> [!Discussion]
> Alternatively, we could select just the `dept_name` column from the `departments` table.
2.  Write a query to get the details for the first 25 employees in the employee table ordered by first name, descending. 
   ![Pasted image 20230329194553.png](/img/user/Attachments/Pasted%20image%2020230329194553.png)
> [!Discussion]
> The results for this query would be more useful if sorted by last name after the first name, like this:
> 
> `ORDER BY first_name DESC, last_name DESC`
> 
> Try making this change to the query and compare the new results to the original results.
   
3.  Write a query to display the first 10 employee names (first_name, last_name) using the alias name “First Name", "Last Name”.  
![Pasted image 20230329194722.png](/img/user/Attachments/Pasted%20image%2020230329194722.png)

4.  How many male employees are there?  How many female employees?
![Pasted image 20230329194911.png](/img/user/Attachments/Pasted%20image%2020230329194911.png)
> [!Discussion]
> We can obtain these totals using separate queries.  However, it can be done in a single query – using the `GROUP BY` clause together with the `COUNT` function allows us to obtain a subtotal for each unique value found in the `gender` column.

5.  Write a query that lists all the salaries for employees in the company, in ascending order.   
![Pasted image 20230329195322.png](/img/user/Attachments/Pasted%20image%2020230329195322.png)
> [!Discussion]
> Apologies as this query may have taken a long time to execute on your computer. It took almost four seconds with an M1 Pro processor; this took a lot longer to run on Macs with older processors.

6.  Write a query that lists all the salaries for employees in the company, in descending order.  
![Pasted image 20230329195708.png](/img/user/Attachments/Pasted%20image%2020230329195708.png)

7.  Write a query to get the total salaries payable to employees.
![Pasted image 20230329200012.png](/img/user/Attachments/Pasted%20image%2020230329200012.png)
> [!Discussion]
> Use of the alias:
> 
> `SUM(salary) AS "Total salaries payable"`
> 
> ...is not strictly required, but helps to make the results more readable, since the column title will show as `"Total salaries payable"` rather than `SUM(salary)`.

8.  What is the average salary for all employees?  
![Pasted image 20230329200216.png](/img/user/Attachments/Pasted%20image%2020230329200216.png)

9.  How many employees work for the company?
![Pasted image 20230329200927.png](/img/user/Attachments/Pasted%20image%2020230329200927.png)

10.  Find a list of employee IDs where the salary paid is greater than $60000.  
![Pasted image 20230329201706.png](/img/user/Attachments/Pasted%20image%2020230329201706.png)
> [!Discussion]
> The `WHERE` clause is useful for filtering the list of rows that are returned based on some provided criteria – in this case – only rows where the salary value is more than $60000 are returned.
> 
> An alternate solution to this question provides a list of employee ID's without duplicates, by adding the `GROUP BY` clause:
> 
> `SELECT emp_id`
> `FROM salaries`
> `WHERE salary > 60000`
> `GROUP BY emp_id`
> 
> ![Pasted image 20230329201553.png](/img/user/Attachments/Pasted%20image%2020230329201553.png)

11.  _How many_ employee IDs have been tied to a salary that is greater than $60000?  
![Pasted image 20230329201914.png](/img/user/Attachments/Pasted%20image%2020230329201914.png)
> [!Discussion]
> Here we begin making use of sub-queries.
> 
> Think of this as a two-step process.
> 
> First – with the innermost query – the sub-query – we find the list of unique employee ID's tied to at least one salary that was greater than $60000.
> 
> Then – with the outer query – we count the number of rows returned by the sub-query.

{ #6b37ef}

12.  Find a list of employee IDs where the salary paid is in the range $60000 to $70000.  
![Pasted image 20230329202205.png](/img/user/Attachments/Pasted%20image%2020230329202205.png)
> [!Discussion]
> Here is an alternate solution to this question:
> 
> ![Pasted image 20230329202406.png](/img/user/Attachments/Pasted%20image%2020230329202406.png)
> 
> Consider – which syntax do you prefer? Is one version of this query clearer than the other with regard to what range of values it is looking for?

13.  _How many_ employee IDs have been tied to a salary in the range $60000 to $70000?  
![Pasted image 20230329202607.png](/img/user/Attachments/Pasted%20image%2020230329202607.png)
> [!Discussion]
> Here a sub-query is used again.
> 
> The innermost query is the same as the solution to question #12. It returns all the rows where an employee was at least once tied to a salary in the desired range.
> 
> The outermost query counts how many rows were returned in the sub-query.

14.  Find a list of employee IDs whose salary is *not* in the range $60000 to $70000.  
![Pasted image 20230329203043.png](/img/user/Attachments/Pasted%20image%2020230329203043.png)
> [!Discussion]
> The `NOT` keyword provides the logical inverse of the set of rows returned by the query from question #12.
> 
> At first glance, the results above may seem incorrect.
> 
> For instance: how can the employee with ID 10001 have a a salary that is both between $60000 and $70000 and *outside* of that range?
> 
> That is possible because the employee had different salaries at different points in time.
> 
> This becomes apparent if we adjust the results of the query by removing the `GROUP BY` clause and taking a look at the data in all four columns:
> 
> ![Pasted image 20230329203517.png](/img/user/Attachments/Pasted%20image%2020230329203517.png)
> 
> We can see that as time went on, the employee with ID 10001 received several raises. We can infer that prior to June 25, 1991 the same employee had a salary lower than $70000, which is why that employee ID also shows up in the rows returned by the query from question #12.

15.  Find only the maximum and minimum salary paid to employee number 10012.  
![Pasted image 20230329203959.png](/img/user/Attachments/Pasted%20image%2020230329203959.png)
> [!Discussion]
> Try running just the following query:
> 
> `SELECT`
> `    salary`
> `FROM salaries`
> `WHERE emp_id = 10012`
> 
> You will see the set of rows showing all salaries that have been tied to employee ID 10012.
> 
> By adding the `MAX` and `MIN` functions to the query, we are picking out only the highest and lowest values in the list of rows returned by the simpler query.

16.  Find the maximum and minimum salary paid to all employees.  
![Pasted image 20230329204257.png](/img/user/Attachments/Pasted%20image%2020230329204257.png)
> [!Discussion]
> Without the `GROUP BY` clause we would get the maximum and minimum salary paid to the entire set of employees at the company. That is, the highest single salary paid to anyone, and the lowest single salary paid to anyone.
> 
> By using the `GROUP BY` clause on the `emp_id` column, we are telling the database to give us the maximum and minimum salary for each individual employee at the company.

17.  Write a query to display the first name and last name of all employees who have both "b" and "c" in their first name.  Order the results by first name, then by last name.
![Pasted image 20230329204630.png](/img/user/Attachments/Pasted%20image%2020230329204630.png)
> [!Discussion]
> Sorting by first name and then last name as well was not required, but makes the results easier for a human being to review.

18.  Find a list of all the job titles held by employee number 499998. List the job titles in alphabetical order.
![Pasted image 20230329204821.png](/img/user/Attachments/Pasted%20image%2020230329204821.png)

<small>[[Current Courses/Grade 11 Introduction to Computer Science/Solutions/Databases#Databases\|Back to top ⬆]]</small>
