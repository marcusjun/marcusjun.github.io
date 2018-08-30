---
layout: post
title:      "SQL labs: random tips and tricks"
date:       2018-08-30 00:09:25 +0000
permalink:  sql_labs_random_tips_and_tricks
---


- When I'm writing SQL code, I format it so that it's readable to me and organized in a way that makes sense to me.

So I'll use white spacing and new lines to declutter the code.

For example, when I'm inserting rows into a table, I could write the SQL command as one line but I spaced out the code so it's easier for me to read and also check for errors.

```
INSERT INTO books (title, year, series_id) VALUES
("Shadowlands", 1999, 1),
("Tundralands", 2000, 1),
("Cloudlands", 2001, 1);
INSERT INTO books (title, year, series_id) VALUES
("Begin-inings", 2007, 2),
("Middling-ings", 2008, 2),
("Ending-ings", 2009, 2);
```

and same with my SQL queries, (it's easier for me to read what each line of the query is doing)
```
"SELECT projects.title, SUM(pledges.amount) - projects.funding_goal
FROM projects
INNER JOIN pledges
ON projects.id = pledges.project_id
GROUP BY projects.title
HAVING SUM(pledges.amount) >= projects.funding_goal;"
```

- When I'm writing the SQL queries, it's a lot of trial and error and "copying" queries from the lessons and trying to make the query fit the lab's requirements. I try to change one segment of code at a time and run the learn command to check my work. If I get stuck, I'll go backward to a broader query and make sure that I can at least get some results for my query. Then I'll narrow down my query to fit the lab specs.

- The error messages when you run the lab specs are helpful too. I compare what the lab expects the SQL query to return versus what my SQL query actually returns and try to figure out what's wrong with my query. 

- Another helpful tool is the split window in the Learn IDE interface. So on the left I'll have the "schema.sql" open to see how the SQL data is organized and on the left I'll have the SQL code the queries the data.


