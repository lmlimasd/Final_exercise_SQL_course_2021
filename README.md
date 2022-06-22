# Final exercise course 
### SQL for Data Science - Coursera 2021 - University of California, Davis 
<p>As the final exercise in the course SQL for Data Science. This assignment is designed to test the knowledge of a wide range of concepts and SQL design techniques discussed throughout the course. Using a dataset from a US-based organization called <a href="https://www.yelp.com/dataset" target="blank">Yelp Open Dataset</a> , which provides a platform for users to provide reviews and rate their interactions with a variety of organizations – businesses, restaurants, health clubs, hospitals, local governmental offices, charitable organizations, etc. Yelp has made a portion of this data available for personal, educational, and academic purposes. Check out the Yelp Dataset ER Diagram and instructions below for more detailed information on the dataset and how was completed the assignment.</p>

<p><a>Note: </a> For most information about the Dataset visit:</p>

<ul>
<li> <a href="https://www.yelp.com/dataset" target="blank">Yelp Dataset</a> </li>
<li> <a href="https://github.com/Yelp/dataset-examples" target="blank">Repository Yelp's Academic Dataset Examples</a></li>
</ul>


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

<table class="tg">
  <thead>
      <tr>
          <th >City</th>
          <th >All_reviews_by_city </th>
      </tr>
  </thead>
  <tbody>
      <tr>
        <td>Las Vegas
          <br>Phoenix
          <br>Toronto
          <br>Scottsdale
          <br>Charlotte
          <br>Henderson
          <br>Tempe
          <br>Pittsburgh
          <br>Montréal
          <br>Chandler 
          <br>Mesa
          <br>Gilgert
          <br>Cleveland
          <br>Madison
          <br>Glendale
          <br>Mississauga
          <br>Edinburgh
          <br>Peoria
          <br>North Las Vegas
          <br>Markham
          <br>Champaign
          <br>Stuttgart
          <br>Surprise
          <br>Lakewood
          <br>Goodyear
        </td>
        <td>82854<br>34503<br>24113<br>20614<br>12523<br>10871<br>10504<br>9798<br>9448<br>8112<br>6875<br>6380<br>5593<br>5265<br>4406<br>3814<br>2792<br>2624<br>2438<br>2352<br>2029<br>1849<br>1520<br>1465<br>1155</td>
      </tr>
  </tbody>
</table>

```diff
-- Code Used --
+ SELECT city
+      ,SUM(review_count) AS All_reviews_by_city
+ FROM business
+ GROUP BY city
+ ORDER BY all_reviews_by_city DESC
```

<!-- Parte 6 -->
<h4 style="color:#0080c0">6. Find the distribution of star ratings to the business in the following cities:</h4>

<p><a>Avon:</a></p>

<p><a>Answer:</a></p>

<table >
<thead>
  <tr>
    <th >Star rating</th>
    <th >count</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td >1.5<br>2.5<br>3.5<br>4.0<br>4.5<br>5.0</td>
    <td >10<br>6<br>88<br>21<br>31<br>3<br></td>
  </tr>
</tbody>
</table>

```diff
-- Code Used --
+ SELECT stars AS "Star rating"
+      ,sum(review_count) AS "count"
+ FROM business
+ WHERE city == "Avon"
+ GROUP BY stars
```


<!-- Parte 7 -->
<h4 style="color:#0080c0">7. Find the top 3 users based on their total number of reviews</h4>

<p><a>Answer:</a></p>

<table>
<thead>
  <tr>
    <th>name</th>
    <th>total number of reviews</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Gerald<br>Sara<br>Yuri</td>
    <td>2000<br>1629<br>1339</td>
  </tr>
</tbody>
</table>


```diff
-- Code Used --
+ SELECT name
+      ,sum(review_count) AS "total number of reviews"
+ FROM user
+ GROUP BY id
+ ORDER BY sum(review_count) DESC
+ LIMIT 3
```

<!-- Parte 8 -->
<h4 style="color:#0080c0">8. Does posing more reviews correlate with more fans?</h4>

<p><a>Answer:</a></p>  <p>Tables 1 and 2 compare the number of reviews vs the number of fans. It is observed that only the user Gerald has a considerable number of reviews and fans, while the rest of the user varies his position in the top. So it can be concluded that there is NO CORRELATION BETWEEN a greater number of reviews and a greater number of fans.</p>


<p>Table 1. Total_ reviews vs Total_fans. Order by number of reviews in form descendent.</p> 
<table>
<thead>
  <tr>
    <th>name </th>
    <th>total number of reviews </th>
    <th>total number of fans  </th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Gerald
      <br>Sara
      <br>Yuri
      <br>.Hon
      <br>William
    </td>
    <td>2000
      <br>1629
      <br>1339
      <br>1246
      <br>1215
    </td>
    <td>253
      <br>50
      <br>76
      <br>101
      <br>126
    </td>
  </tr>
</tbody>
</table>

<p>Table 2. Total_ reviews vs Total_fans. Order by number of fans in form descendent.</p> 
<table>
<thead>
  <tr>
    <th>name </th>
    <th>total number of reviews </th>
    <th>total number of fans  </th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Amy  
      <br>Mimi
      <br>Harald
      <br>Gerald
      <br>Christine
    </td>
    <td>609 
      <br>968
      <br>1153
      <br>2000
      <br>930
    </td>
    <td>503
      <br>497
      <br>311
      <br>253
      <br>173
    </td>
  </tr>
</tbody>
</table>

```diff
-- Code Used --
+ SELECT name
+      ,sum(review_count) AS "total number of reviews"
+      ,sum(fans) AS "total number of fans"
+ FROM user
+ GROUP BY id
+ ORDER BY sum(review_count) DESC -- table 1
+ ORDER BY sum(fans) DESC -- table 2

```

<!-- Parte 9 -->
<h4 style="color:#0080c0">8. Does posing more reviews correlate with more fans?</h4>

<p><a>Answer:</a></p> YES, there are 1780 reviews with the word "love" and only 232 reviews with the word "hate".<p></p>

```diff
-- Code Used --
+ SELECT (SELECT count(id)
+        From review
+        WHERE text LIKE "%love%") AS "love"
+      ,(SELECT count(id)
+        From review
+        WHERE text LIKE "%hate%") AS "hate"
```

<!-- Parte 10 -->
<h4 style="color:#0080c0">8. Find the top 10 users with the most fans:</h4>

<p><a>Answer:</a></p> YES, there are 1780 reviews with the word "love" and only 232 reviews with the word "hate".<p></p>

<table>
<thead>
  <tr>
    <th>name </th>
    <th>number of fans </th>
    <!-- <th>total number of fans  </th> -->
  </tr>
</thead>
<tbody>
  <tr>
    <td>Amy  
    <br>Mimi
    <br>Harald
    <br>Gerald
    <br>Christine
    <br>Lisa
    <br>Cat
    <br>William
    <br>Fran
    <br>Lissa  
    </td>
    <td>503
    <br>497
    <br>311
    <br>253
    <br>173
    <br>159
    <br>133
    <br>126
    <br>124
    <br>120
    </td>
    <!-- <td>503
      <br>497
      <br>311
      <br>253
      <br>173
    </td> -->
  </tr>
</tbody>
</table>

```diff
-- Code Used --
+	SELECT name
+      ,SUM(fans) AS "number of fans"
+ FROM user
+ GROUP BY Id
+ ORDER BY fans DESC
+ LIMIT 10
```

<!-- Parte 11 -->
<h4 style="color:#0080c0">8. Find the top 10 users with the most fans:</h4>

<p><a>Answer:</a></p> YES, there are 1780 reviews with the word "love" and only 232 reviews with the word "hate".<p></p>


# Part 2

you are asked to come up with your own inferences and analysis of the data for a particular question you want to answer. You will be required to prepare the dataset for the analysis you choose to do. As with the first part, you will be graded, in part, on how easy your code is to read, so use proper formatting and comments to illustrate your intent as required.
