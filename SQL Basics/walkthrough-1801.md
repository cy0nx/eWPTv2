![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.001.png)

![ref1]
<table><tr><th colspan="1"><b>Name</b> </th><th colspan="1">SQL Basics </th></tr>
<tr><td colspan="1" rowspan="2"><b>URL</b> </td><td colspan="1" valign="bottom"><https://attackdefense.com/challengedetails?cid=1801> </td></tr>
<tr><td colspan="1"></td></tr>
<tr><td colspan="1"><b>Type</b> </td><td colspan="1">Webapp Pentesting Basics </td></tr>
</table>

**Important Note:** This document illustrates all the important steps required to complete this lab. This  is  by  no  means  a  comprehensive  step-by-step  solution for this exercise. This is only provided as a reference to various commands needed to complete this exercise and for your further research on this topic. Also, note that the IP addresses and domain names might be different in your lab.  

In  this exercise, we will take a look at basic SQL queries this includes usage of SELECT, CREATE, INSERT, UPDATE, UNION and JOIN statements. 

**Home Page:  ![ref2]**

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.004.jpeg)

**Enter the Credentials:** 

**Username:** admin **Password:** admin 

**Step 1:** Expand the Databases section on the Left Panel and click on any of the table from the wpdatabase. ![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.005.jpeg)![ref2]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.006.jpeg)


![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.007.png)

Information regarding the table is displayed in the Properties tab. **Step 2:** Click on the DDL Tab. 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.008.jpeg)

The table definition is mentioned on the DDL tab. ![ref2]

**Step 3:** Expand "wp\_commentmeta" table and the child tree.  

![ref1]

The columns, primary key, foreign key and Indexes information can be accessed from the left section. ![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.009.jpeg)

**Step 4:** Expand the columns.  ![ref2]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.010.jpeg)

The datatype and properties of the columns are displayed.  

**Getting started with basic SQL Queries**  

**Task  1:** Identifying the databases present on the system. **Query:** show databases; 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.011.jpeg)

**Task 2:** Selecting a database. ![ref2]**Query:** use wpdatabase; 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.012.jpeg)

**Task 3:** Listing tables in a database. **Query:** show tables; 


![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.013.png)

**Task 4:**  Retrieving Data from the table. **Query:** select \* from wp\_users; ![ref2]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.014.jpeg)

![ref1]

**Task 5:** Retrieving data from only certain columns of a table. **Query:** select user\_login,user\_pass from wp\_users; 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.015.jpeg)

**Task 6:** Retrieving data from table by mentioning the database name. **Query:** select \* from wpdatabase.wp\_posts; 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.016.png)


![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.017.png)

**Task 7:** Sorting data on the basis of post title. 

**Query:** select \* from wpdatabase.wp\_posts order by post\_title; 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.018.jpeg)

**Task 8:** Retrieving first record from the table. ![ref2]

**Query:** select \* from wpdatabase.wp\_posts order by post\_title limit 1; 

![ref1]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.019.jpeg)

**Task 9:** Retrieving a particular row from the table. 

**Query:** select \* from wpdatabase.wp\_posts order by post\_title limit 2,1;** 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.020.jpeg)

**Task 10:** Create a new table "new\_users" with name, email and id as columns. Use the id column as a primary key.  

**Query:** create table new\_users (     name varchar(100), ![ref2]

`    `email varchar(100), 


`    `id varchar(100),     primary key(id) ) ![ref1]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.021.jpeg)

**Task 11:** Inserting rows into the table. 

**Query:** insert into wpdatabase.new\_users values ("John","john@attackdefense.com","pa-01234"); 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.022.jpeg)

**Task 12:** Updating record in the table. ![ref2]

**Query:** update wpdatabase.new\_users set name="james" where id="pa-01234"; 

![ref1]

**Task 13:** Combining records from two tables using UNION Statement, UNION statement requires equal number of columns to be selected from each table. ![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.023.jpeg)

Checking columns in wp\_users table **Query:**  desc wpdatabase.wp\_users; ![ref2]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.024.jpeg)

Checking columns in new\_users table (created in Task 10). **Query:** desc wpdatabase.new\_users; 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.025.jpeg)

Union query:  

**Query:** select user\_login,user\_email from wpdatabase.wp\_users union select name,email from wpdatabase.new\_users; 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.026.png)


![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.027.png)

The data from the tables wp\_users and new\_users was presented in a single table. 

**Task 14:** Insert more data into the new\_users table and use the JOIN statement to retrieve the users who have common name in new\_users and wp\_users table. 

Inserting user named admin to new\_users table. 

**Query:** insert into wpdatabase.new\_users values("admin","admin@admin.xyz","pa-02333"); 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.028.jpeg)

Similarly insert user "jimmy" and "david". 

**Query:** insert into wpdatabase.new\_users values("jimmy","jimmy@attackdefense.com","pa-02323"); ![ref2]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.029.png)

**Query:** insert into wpdatabase.new\_users values("david","<david@attackdefense.com>","pa-02663"); 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.030.jpeg)

Viewing records in table new\_users: ![ref2]

**Query:** select \* from wpdatabase.new\_users; 

![ref1]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.031.jpeg)

Using a JOIN statement to combine rows from new\_users and wp\_users table. 

**Query:** select \* 

from wpdatabase.wp\_users 

JOIN wpdatabase.new\_users on wpdatabase.new\_users.name=wpdatabase.wp\_users.user\_login ![ref2]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.032.jpeg)

The columns from both the tables are returned in the data. 

**Task 15:** Using the join statement, display the value in user\_login and user\_pass field from the table wp\_users and display the id from new\_users table. 

**Query:** select wpdatabase.wp\_users.user\_login,wpdatabase.wp\_users.user\_pass,wpdatabase.new\_users.id from wpdatabase.wp\_users JOIN wpdatabase.new\_users on wpdatabase.new\_users.name=wpdatabase.wp\_users.user\_login 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.033.jpeg)

**Task 16:** Use an alias "name" and "password" for the column user\_login,user\_pass respectively in the table wp\_users. 

**Query:** select user\_login as name, user\_pass as password from wpdatabase.wp\_users; 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.034.png)


![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.035.png)

**Task 17:** Identify the distinct authors who have published a post. The post\_author column in wp\_posts table consists the id of authors. 

**Query:** select distinct(post\_author) from wpdatabase.wp\_posts;** 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.036.jpeg)

Only 1 author has published a post.  ![ref2]

**Task 18:** Count the posts stored in the wp\_posts table. Use the COUNT aggregate function. **Query:** select count(\*) from wpdatabase.wp\_posts; 

![ref1]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.037.jpeg)

**Task 19:** Show all the data of the posts which have the status "publish". **Query:** select \* from wpdatabase.wp\_posts where post\_status='publish'; ![ref2]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.038.jpeg)

**Task 20:** Show all the data of the posts which have "wp:paragraph" in it's content. Use the Like clause 

**Query:** select \* from wpdatabase.wp\_posts where post\_content like '%wp:paragraph%'; 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.039.jpeg)

**Task 21:** Show all the data for the posts which have post\_status set to "publish" and comment\_status set to "closed". 

**Query:** select \* from wpdatabase.wp\_posts where post\_status="publish" and comment\_status="closed" 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.040.png)

The Data present in the table can also be viewed by right clicking the table name from the left panel and selecting the Query data option. ![ref2]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.041.jpeg)

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.042.jpeg)

Similarly, OmniDB also provides option to EDIT table ,INSERT, Update records: EDIT Table: ![ref2]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.043.jpeg)

Insert record:  

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.044.jpeg)

Update record:  ![ref2]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.045.jpeg)

**Getting Started with PHPMyAdmin Login Page:  ![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.046.jpeg)**

The login credentials are mentioned in the challenge description.  

Username: root 

Password: Blank or <No Password> 

**Main Dashboard:  ![ref2]**


The databases are listed on the Left Panel. Expand the wpdatabase. ![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.047.jpeg)![ref1]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.048.png)

![ref1]

**All the tables present inside the database are displayed. Expand the wp\_users table.** 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.049.jpeg)

The information regarding the columns and the indexes are displayed on the left panel. **Clicking on the Databases Tab.**  

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.050.png)

All the Databases are listed on the web page. **Click on the wpdatabase Table** 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.051.jpeg)

The tables inside the database wpdatabase are displayed.  ![ref2]**Click on the Table wp\_users** 

The record of the tables are displayed on the web page.  ![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.052.jpeg)

**Click on the Structure tab to see the structural information of the tables.**  

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.053.png)

**Click on the SQL tab.**  

The SQL queries can be executed on the SQL tab. The same queries which were executed on the OmniDB SQL console can be executed here. The various buttons provided on the page "select", "insert", "update" can be used to change the statement.  ![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.054.jpeg)![ref2]

**Click on the Search Tab** 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.055.jpeg)

The search tab provides an easy way to search the table instead of writing SELECT statements with where clause. The values can be directly set to value with various operators.  ![ref2]

**Click on the Insert Tab: ![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.056.jpeg)**

The Insert tab functionality can be used to insert records into the table.  ![ref2]

**Click on the Export Tab:**  

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.057.jpeg)

Specific Table can be exported from the export table. ![ref2]

Click on the Import section  

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.058.jpeg)

The import section can be used to import an SQL archive file into the tables. ![ref2]**Click on the Privileges Tab** 

The privileges to the wpdatabase table are mentioned on the tab. ![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.059.jpeg)**Click on the Operations tab.** 

Operations such as moving the table, creating a copy, renaming it, adding comments can be performed from the operations tab.  ![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.060.jpeg)![ref2]

**Click on Triggers** 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.061.jpeg)

The triggers are mentioned here. Currently there are no triggers.  **Click on the Dashboard** (Home Icon) 

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.062.png)

**Click on the SQL Tab. ![ref2]**


![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.063.png)

The SQL statements can be executed from here. All the statements executed above on the OmniDB SQL console can be executed here.  

**Click on the User accounts Tab.  ![ref2]**

![ref1]

![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.064.jpeg)

Access to various User accounts are mentioned on the web page. ![ref2]**Click on the Binary Log** 


![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.065.png)

The Binary log tab displays all the SQL queries executed. ![](Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.066.jpeg)![ref2]

![ref1]

**References:**  

1. OmniDB (<https://omnidb.org/en/>) ![ref2]
1. PHPMyAdmin (<https://www.phpmyadmin.net/>) 

[ref1]: Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.002.png
[ref2]: Aspose.Words.081b1fe6-c3b5-490e-b782-2e6f78e086f8.003.png
