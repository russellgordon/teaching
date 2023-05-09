---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/concepts/databases-joining-tables/","dgHomeLink":false}
---


# Joining Tables in a Database

## Motivation for Joining Tables

When writing queries for [[Current Courses/Grade 11 Introduction to Computer Science/Concepts/Databases\|yesterday's exercise]], you might have been forgiven for wondering whether some of the queries were very useful.

For example, consider the solution to exercise 10:

![Pasted image 20230330054012.png](/img/user/Attachments/Pasted%20image%2020230330054012.png)

Human beings generally don't do well with memorizing a lot of numeric IDs.

In addition to the ID number, to be truly useful, what we'd really like to see is the *name* of employee 10001, 10002, and so on.

Recall that this is the structure of the database in question:

![Pasted image 20230328060245.png](/img/user/Attachments/Pasted%20image%2020230328060245.png)

The `salaries` table holds the salary information we need, but not the employee names:

![Pasted image 20230330054525.png](/img/user/Attachments/Pasted%20image%2020230330054525.png)

The `employees` table holds the names we want to see, but not the salary information:

![Pasted image 20230330054631.png](/img/user/Attachments/Pasted%20image%2020230330054631.png)

What piece of information do both tables have in common?

What information *joins* a row of data from one table to the other?

If you look closely, you will see that this is the **employee ID**, or `emp_id`.

We can select columns from both tables if we *join* the tables on the information that they have in common.

## Joining Tables

Here is a query that selects all columns from the `employees` table:

![Pasted image 20230330055958.png](/img/user/Attachments/Pasted%20image%2020230330055958.png)

> [!NOTE]
> We limit the results to just 25 rows to ensure the query runs quickly. Using the LIMIT clause has nothing to do with joining tables.

And here is a query that selects all columns from the `salaries` table:

![Pasted image 20230330060021.png](/img/user/Attachments/Pasted%20image%2020230330060021.png)

Here is a query that *joins* the tables so that we can see names next to salary information:

![Pasted image 20230330060358.png](/img/user/Attachments/Pasted%20image%2020230330060358.png)

Note that the `emp_id` column is repeated, because that data exists in both tables – it's the column we used to join the tables together:

![Pasted image 20230330061638.png](/img/user/Attachments/Pasted%20image%2020230330061638.png)

To be completely clear, let's break that query down line by line, referring to the line numbers shown in the screenshot.

---

	73: SELECT * 

All columns are selected.

---

	74: FROM employees

We have to start somewhere, so first we select from the `employees` table.

---

	75: INNER JOIN salaries

We tell the database that we also want columns from the `salaries` table. 

---

	76: ON employees.emp_id = salaries.emp_id

To join tables, the database needs to know what columns contain identical information in each table. That's the `emp_id` column.

---

	77: LIMIT 25

This has nothing to do with joining tables and is included just so the query runs quickly.

## Improving the Original Query

Of course, we do not have to select *every* column from both tables when performing a join.

Let's return to the original query we examined:

![Pasted image 20230330054012.png](/img/user/Attachments/Pasted%20image%2020230330054012.png)

We can make this query more useful – if we join the employees table based on the fact that we know the `emp_id` column contains identical information:

![Pasted image 20230330063133.png](/img/user/Attachments/Pasted%20image%2020230330063133.png)

Now we have each employee ID right next to the employee's name. 🎉

> [!NOTE]
> On line 80 we had to specify the table name when indicating that we want to select the employee ID:
> 
> ![Pasted image 20230330063240.png](/img/user/Attachments/Pasted%20image%2020230330063240.png)
> 
> Why did we have to do this?
> 
> If you're not sure, please review the lesson above, taking care to observe the results when all columns are selected from two joined tables.
> 
> Or, try running this query again without  `salaries.` in front of the `emp_id` column identifier. What error message do you receive from the database?

## Final notes

You might wonder – how do you know what column to use when joining tables?

In the example above, you were walked through the join operation. 

How would you know, on your own, what columns to use?

The answer lays in the database structure diagram:

![Pasted image 20230330071652.png](/img/user/Attachments/Pasted%20image%2020230330071652.png)

Notice that the `emp_id` column appears in both the `employees` table and the `titles` table.

The identical column is connected by a line between those tables.

This is your visual cue – look for the same column name in both tables, and the connecting line.

## Exercise

Most of the questions below were originally part of the [[Current Courses/Grade 11 Introduction to Computer Science/Concepts/Databases#Exercise\|prior day's exercise]].

Improve these queries by joining between tables to obtain more useful results.

1.  Find a list of employees where the salary paid is in the range $60000 to $70000.  
   <sub>*Originally question 12.*</sub>

2.  Find a list of employees whose salary is *not* in the range $60000 to $70000.  
   <sub>*Originally question 14.*</sub>
   
3.  Find the maximum salary, minimum salary, first name, and last name for employee number 10012.
<sub>*Originally question 15.*</sub>

4.  Find the maximum and minimum salary paid to all employees.  Include employee names.
<sub>*Originally question 16.*</sub>

5.  Find a list of all the job titles held by employee number 499998, and their name. List the job titles in alphabetical order.
<sub>*Originally question 18.*</sub>

6. Now come up with your own interesting question to ask regarding this company and its employees. Then, write a query to answer your question.
   
   Here are some examples...
   
   - Which employee has held the most job titles?
   - Who was the youngest employee ever hired by the company, and when did that occur?
   - Who were the ten people most recently hired at the company?
