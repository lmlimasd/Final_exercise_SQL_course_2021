# Final exercise course 
### SQL for Data Science - Coursera 2021 - University of California, Davis 
<p>As the final exercise in the course SQL for Data Science. This assignment is designed to test the knowledge of a wide range of concepts and SQL design techniques discussed throughout the course. Using a dataset from a US-based organization called <a href="https://www.yelp.com/dataset" target="blank">Yelp Open Dataset</a> , which provides a platform for users to provide reviews and rate their interactions with a variety of organizations – businesses, restaurants, health clubs, hospitals, local governmental offices, charitable organizations, etc. Yelp has made a portion of this data available for personal, educational, and academic purposes. Check out the Yelp Dataset ER Diagram and instructions below for more detailed information on the dataset and how was completed the assignment.</p>



## Yelp Dataset ER Diagram

The entity relationship (ER) diagram below, should help familiarize you with the design of the Yelp Dataset provided for this peer review activity.

<p><img src="ER_diagram.png"
     alt="Markdown Monster icon"   style= "max-width: 80%; height auto;" />
</p>
Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.
<p>

</p>



<h2 style="color:#0080c0">First Part</h2>

you are asked a series of questions that will help you profile and understand the data just like a data scientist would. For this first part of the assignment, you will be assessed both on the correctness of your findings, as well as the code you used to arrive at your answer. You will be graded on how easy your code is to read, so remember to use proper formatting and comments where necessary.


<h4 style="color:#0080c0">1. Profile the data by finding the total number of records for each of the tables below:</h4>

<p><a>Answer:</a> The dataset have 11 tables with 10.000 rows every each.</p>

<p style="color:#0080c0">SQL code used to arrive at answer:</p>

```diff
+ SELECT COUNT(*) 
+ FROM "name of the table"
```

<h4 style="color:#0080c0">2. Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key:</h4>

<p><a>Answer:</a>


<ul style= "list-style-type: upper-roman;">
<li>Business = (PK), id= 10000 </li>
<li>Hours = (FK), business_id= 1562. </li>
<li>Category = (FK), business_id= 2643.</li>
<li>Attribute = (FK), business_id= 1115.</li>
<li>Review = (PK), id=10000, (FK) business_id= 8090, (FK)User_id= 9581. </li>
<li>Checkin = (FK), business_id= 493. </li>
<li>Photo = (PK), id=10000, (FK)business_id= 6493. </li>
<li>Tip = (FK), User_id= 537, (FK)business_id= 3979. </li>
<li>User = (PK),id=10000.</li>
<li> Friend = (FK), User_id= 11, (FK)</li>
<li>Elite_years = (FK), User_id= 2780.</li>
</ul>


<p style="color:#0080c0">SQL code used to arrive at answer:</p>

```diff
+ SELECT count(DISTINCT /*Primary or Foreign Key*/)
+ FROM -- Table
```

<h4 style="color:#0080c0">3. Are there any columns with null values in the Users table? Indicate "yes," or "no."</h4>

<p><a>Answer: NO</a>

<p style="color:#0080c0">SQL code used to arrive at answer:</p>


```diff
-- Code Used --
+ SELECT COUNT(*)
+ FROM User 
+ WHERE id IS NULL 
+      OR name IS NULL
+      OR review_count IS NULL
+      OR yelping_since IS NULL
+      OR useful IS NULL
+      OR funny IS NULL
+      OR cool IS NULL
+      OR fans IS NULL
+      OR average_stars IS NULL
+      OR compliment_hot IS NULL
+      OR compliment_more IS NULL
+      OR compliment_profile IS NULL
+      OR compliment_cute IS NULL
+      OR compliment_list IS NULL
+      OR compliment_note IS NULL
+      OR compliment_plain IS NULL
+      OR compliment_cool IS NULL
+      OR compliment_funny IS NULL
+      OR compliment_writer IS NULL
+      OR compliment_photos IS NUL
```

# Part 2

you are asked to come up with your own inferences and analysis of the data for a particular question you want to answer. You will be required to prepare the dataset for the analysis you choose to do. As with the first part, you will be graded, in part, on how easy your code is to read, so use proper formatting and comments to illustrate your intent as required.
