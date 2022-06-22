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

```diff
-- Code Used --
+ SELECT COUNT(*) 
+ FROM "name of the table"
```

<h4 style="color:#0080c0">2. Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key:</h4>

<p><a>Answer:</a></p>


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




```diff
-- Code Used --
+ SELECT count(DISTINCT /*Primary or Foreign Key*/)
+ FROM -- Table
```

<h4 style="color:#0080c0">3. Are there any columns with null values in the Users table? Indicate "yes," or "no."</h4>

<p><a>Answer: NO</a></p>

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
<!-- Parte 4 -->
<h4 style="color:#0080c0">4. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:
</h4>

<p><a>Answer:</a></p>


<ul style= "list-style-type: upper-roman;">
<li>Table: Review, Column: Stars</li>
<p>min:	1.0	max:	5.0	avg:	3.7082</p>

<li>Table: Business, Column: Stars</li>
<p>min:	1.0	max:	5.0	avg:	3.6549</p>

<li>Table: Tip, Column: Likes</li>
<p>min:	0	max:	2	avg:	0.0144</p>

<li>Table: Checkin, Column: Count</li>
<p>min:	1	max:	53	avg:	1.9414</p>

<li>Table: User, Column: Review_count</li>
<p>min:	0	max:	2000	avg:	24.2995</p>
</ul>

```diff
-- Code Used --
+SELECT MIN(/*Name of the column*/) AS "MIN"
+      ,MAX(/*Name of the column*/) AS "MAX"
+      ,AVG(/*Name of the column*/) AS "AVG"
+FROM /*Name of the Table*/
```


<!-- Parte 5 -->
<h4 style="color:#0080c0">List the cities with the most reviews in descending order:</h4>

<p><a>Answer:</a></p>

<!-- <table>
  <thead>
    <tr><th>City</th><th>All reviews by city</th></tr>
  </thead>
  <tbody>
    <tr><td>Las Vegas</td><td>82854</td></tr>
    <tr><td>Phoenix</td><td>34503</td></tr>
    <tr><td>Toronto</td><td>24113</td></tr
    ><tr><td>Scottsdale</td><td>20614</td></tr>
    <tr><td>Charlotte</td><td>12523</td></tr>
    <tr><td>Henderson</td><td>10871</td></tr>
    <tr><td>Tempe</td><td>10504</td></tr>
    <tr><td>Pittsburgh</td><td>9798</td></tr>
    <tr><td>Montréal</td><td>9448</td></tr>
    <tr><td>Chandler</td><td>8112</td></tr>
    <tr><td>Mesa</td><td>6875</td></tr>
    <tr><td>Gilbert</td><td>6380</td></tr>
    <tr><td>Cleveland</td><td>5593</td></tr>
    <tr><td>Madison</td><td>5265</td></tr>
    <tr><td>Glendale</td><td>4406</td></tr>
    <tr><td>Mississauga</td><td>3814</td></tr>
    <tr><td>Edinburgh</td><td>2792</td></tr>
    <tr><td>Peoria</td><td>2624</td></tr>
    <tr><td>North Las Vegas</td><td>2438</td></tr>
    <tr><td>Markham</td><td>2352</td></tr>
    <tr><td>Champaign</td><td>2029</td></tr>
    <tr><td>Stuttgart</td><td>1849</td></tr>
    <tr><td>Surprise</td><td>1520</td></tr>
    <tr><td>Lakewood</td><td>1465</td></tr>
    <tr><td>Goodyear</td><td>1155</td></tr>
  </tbody>
</table> -->

<table style="border-collapse:collapse;border-color:#aabcfe;border-spacing:0;border:none" class="tg"><thead><tr><th style="background-color:#b9c9fe;border-color:#aabcfe;border-style:solid;border-width:0px;color:#039;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">City</th><th style="background-color:#b9c9fe;border-color:#aabcfe;border-style:solid;border-width:0px;color:#039;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">All reviews by city</th></tr></thead><tbody><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Las Vegas</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">82854</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Phoenix</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">34503</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Toronto</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">24113</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Scottsdale</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">20614</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Charlotte</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">12523</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Henderson</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">10871</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Tempe</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">10504</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Pittsburgh</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">9798</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Montréal</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">9448</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Chandler</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">8112</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Mesa</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">6875</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Gilbert</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">6380</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Cleveland</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">5593</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Madison</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">5265</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Glendale</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">4406</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Mississauga</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">3814</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Edinburgh</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">2792</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Peoria</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">2624</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">North Las Vegas</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">2438</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Markham</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">2352</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Champaign</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">2029</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Stuttgart</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">1849</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Surprise</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">1520</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Lakewood</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">1465</td></tr><tr><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">Goodyear</td><td style="background-color:#e8edff;border-color:#aabcfe;border-style:solid;border-width:0px;color:#669;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:0px 10px;text-align:left;vertical-align:top;word-break:normal">1155</td></tr></tbody></table>





```diff
-- Code Used --
+ SELECT city
+      ,SUM(review_count) AS all_reviews_by_city
+ FROM business
+ GROUP BY city
+ ORDER BY all_reviews_by_city DESC
```

<!-- Parte 6 -->
<h4 style="color:#0080c0"></h4>

<p><a>Answer:</a></p>


<ul style= "list-style-type: upper-roman;">
<li></li>
<p></p>


</ul>

```diff
-- Code Used --
+ SELECT city
+      ,SUM(review_count) AS all_reviews_by_city
+ FROM business
+ GROUP BY city
+ ORDER BY all_reviews_by_city DESC
```





# Part 2

you are asked to come up with your own inferences and analysis of the data for a particular question you want to answer. You will be required to prepare the dataset for the analysis you choose to do. As with the first part, you will be graded, in part, on how easy your code is to read, so use proper formatting and comments to illustrate your intent as required.
