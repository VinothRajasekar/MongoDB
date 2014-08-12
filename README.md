MongoDB
=======

MongoDB Analytcis Query implementation using 30 years of NBA dataset

The Dataset
The  dataset put together by Valeri Karpov, a software engineer and data geek/blogger.  (http://thecodebarbarian.wordpress.com/about/ ) He and a friend produced the NBA dataset by scraping data from basketball-reference.com and putting it into a MongoDB friendly format. Details of how they did so, and a basic outline of the data contained in the dataset can be found on his blog entry at:
http://thecodebarbarian.wordpress.com/2014/02/14/crunching-30-years-of-nba-data-with-mongodb-aggregation/

------------------------
Questions of MongoDB NBA:
-------------------------

Question group #1:
Karpov’s blog post has a sample query that calculates how likely a team that has more defensive rebounds than its opponent in a given game is to win that game. He finds there is about a 75.7% likelihood that the winning team also had more defensive rebounds (23,993 wins vs. 7,693 losses).

Modify his query as needed to answer the questions in this question group. You do not necessarily need to have your query compute a final single number. As with the sample query, if you have a pair of values that you can trivially use to compute winning %, that’s fine. Use the values that come out of your query and show your follow-on calculations to compute the appropriate %’s (ie total #wins / total #games). Use the following template for your answers:

a)	Question #.
b)	Brief description of how you modified his query to answer the question.
c)	Answer that you derived from your query and any subsequent calculations of its results. If necessary, add a brief explanation of the answer (no more than a few sentences, shorter is better).
d)	MongoDB query you used to compute the answer to this question.
e)	Exact reproduction of the results of your query, that is, the precise output that MongoDB returns when you run your query. 

Question 1 – What is the likelihood that the team with the higher field goal shooting % in a given game won that game, across all of the games in the dataset?  
•	Note: The field goal shooting % is stored as a percentage value between 0 and 1 in the field box > team > fg_pct.

Question 1a – What is the likelihood that a team with a higher number of field goal attempts in a given game won that game, across all of the games in the dataset?  
Note 1: A field goal attempt is a basket scored while the clock is running and the ball is in play (it does not include free throws granted because of penalties)
Note1: The field goal attempts field is stored in the nba dataset as a numeric value in the field box > team > fga.


Question 2 – Looking only at games played in the 1990’s (January 1, 1990 through December 31, 1999), what is the likelihood that a team with the higher number of blocked shots in a given game won that game, across all of the games in the dataset?  
•	Note: The number of blocked shots in a given game is stored as an integer value field box > team > blk.


Question 3 – Explore a bit how the style of play in the NBA changed over time. What was the relative importance of turnovers in the 1990’s vs. their importance in the 2000’s. That is, what was the likelihood that a team with fewer turnovers in a game won that game in games played in the period 1/1/1990 – 12/31/1999 vs. games played in the period 1/1/2000 – 12/31/2009?


Question group #2:
Please use the following template to answer questions in this group:

a)	Question #.
b)	MongoDB query you used to compute the answer to this question.
c)	Exact reproduction of the results of your query, that is, the precise output that MongoDB returns when you run your query. 

Question 4 – List the five individual players who had the most total rebounds  during the period from 8/1/2000 – 7/31/2005. List their name and their total # of rebounds during that period, in descending order from the player with the most rebounds to the player with the fifth-most rebounds.
•	Note: The number of total rebounds for an individual player in a given game is stored as an integer value field box > players > trb.


Question 5 – Repeat question 4, but this time calculate the five teams with the most total rebounds for all games played during the period 8/1/2000 – 7/31/2005. List the team name and total # of rebounds during the period in descending order.

Question 6 – Show the total points scored by the Detroit Pistons in each year from 2000 – 2009.  That is, you should list each year (2000, 2001, …, 2009) and the total points the team scored in that year. Order your results from the year 2000 to the year 2009.


Question group #3:
Towards the end of Karpov’s blog post he shows a couple of sample queries that attempt to correlate defensive rebounds and total rebounds with winning percentage. The basic idea is that he wants to discover how increasing or decreasing the number of rebounds a team makes in a game increases or decreases their chance of winning that game. The results from these queries are much harder to quickly interpret than the results of the queries in group 1 because they return a long sequence of data rather than two discrete values that can be easily compared. To address this, he imports the data into a graphing program to creata a graph of the results. You need to do the same for your final two queries – convert the JSON result into csv format and graph it with Tableau or Excel. There is a simple JSON to csv conversion tool available at: http://www.convertcsv.com/json-to-csv.htm 

Modify Karpov’s queries as needed to answer these final two questions. Use the following template to answer the questions posed.

a)	Question #.
b)	Brief description of how you modified his query to answer the question.
c)	The MongoDB query you used to compute the answer to this question.
d)	An Excel spreadsheet or Tableau workbook that contains the table with the data you pulled from the query formatted as a table comparing output value with winning %.
e)	A graph showing the relationship between the two values returned, with a computed trendline through the data points.
	
Question 7 – Test the hypothesis that in a given game the team that works together better as a team is more likely to win. Use the number of assists by a team in each game as a proxy for how good their teamwork is. To do so, adapt the query Karpov gives to compare defensive rebounds to winning percentage so that you are comparing the relationship between team assists (box > team > ast) and winning percentage. In addition to completing the answer template, describe how strongly you think your query results support (or disprove) this hypothesis.

Question 8 – Determine whether the total number of personal fouls a team makes in a game (box > team > pf) has a larger affect on winning % than the number of turnovers a team makes in a game (box > team > tov). You may use two separate queries to retrieve the personal fouls and turnover data but for your analysis you should combine the results of those queries into a single table and a single graph that shows trendlines for both personal fouls and turnovers.

-----------------------------

Questions of Mongo Basic NBA:

-----------------------------

Question group #1 (answer any 3):

Question 1 – How many games in the dataset did the Memphis Grizzlies play?

Question 2 – How many games between January 1, 1990 and December 31, 1999 did the Miami Heat play against the Orlando Magic?  

Question 3 – How many NBA games did the Phoenix Suns play between March 1, 1998 and February 5, 2004?

Question 4 – Who played in more NBA games between July 1, 2004 and June 30, 2010: Tim Duncan or Shaquille O'Neal? (you may answer this with one query or use two separate queries and compare the answers by hand)


Question group #2 (answer any 3):

Question 5 – For each game that the Los Angeles Lakers played in 1996, list the following: 
i. the two teams that played in the game (e.g. Los Angeles Lakers and Phoenix Suns)
ii. The final score for the game

Note: you only need to list the first 5 games in the text file you submit for this question, but the query you provide should provide a listing of all of the games that meet the search criteria.


Question 6 – List all games played in 2002 in which the losing team scored less than 75 points. Your query should return the date of the game, the two teams that played, and the final score for each game that meets these criteria. 

As with the previous question, you only need to show the output for first five games returned in your submitted text file, but the query itself should return all the games meeting the criteria.


Question 7 – List all of the teams that the Boston Celtics played between July 1, 2008 and June 30, 2009 when the Celtics were the visiting team. That is, all of the teams that competed against the Celtics when the Celtics were not the home team. Each team that played Boston as the visiting team should be listed exactly once, and only teams that played Boston as the visitors should be listed. Note: the key “home” in each game is true if that team was the home team, false if it was the visitor.

Question 8 – List all of the NBA teams that Shaquille O'Neal played for during his career. Your result should only list the names of each team he played for one time, and should not return any other fields. 

Question 8a – List all of the NBA players that participated in a game with Shaquille O'Neal (Shaq) during the 2006-2007 season, either as a teammate or as a player on the opposing team. You may assume that all games in the 2006-2007 season were played between July 1, 2006 and June 30, 2007. Your result should only list the names of each player one time, and should not return any other fields. Your list may include Shaquille O’Neal. 

The write-up you submit need only list the first five players returned by your query, but when the query is run against the NBA dataset it should return all of the players that meet this criteria. 


Question group #3 (answer any 2):

Question 9 – How many points did Tim Duncan score in 2006?

Question 10 – Extend your answer for question 8 to list both the name of each NBA teams that Shaquille O'Neal played for during his career, and also the total number of games that he played for that team. Your result should only list the names of each team he played for one time, followed by the number of games that he played for that team. 

Question 10a – Extend your answer for question 8 to list the name of each player that ever participated in an NBA game with Shaquille O'Neal as a teammate or on the opposing team, followed by the total number of games that each of those players participated in an NBA game with Shaq. Your result should only list the names of each player one time, followed by the number of games that he played with Shaq. It should be sorted and ordered to first show the player who played in the most games with Shaq, then the player who played in the 2nd most games, on down to the player who played with Shaq in the smallest number of games greater than 0.

