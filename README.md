# sqlcodes
##SUBQUERY

SELECT sub.* 
  FROM (
         SELECT * 
          FROM tutorial.sf_crime_incidents_2014_01
          WHERE day_of_week = 'Friday'
         ) sub
  
  WHERE sub.resolution = 'NONE'
---------------------------------------------
##subquery and aggregation

SELECT LEFT(sub.date,2) AS cleaned_month,
sub.day_of_week,
AVG(sub.incidents) AS average_incidents
FROM (
SELECT day_of_week, 
date,
COUNT(incidnt_num) AS incidents
FROM tutorial.sf_crime_incidents_2014_01
GROUP BY 1,2
) sub
GROUP BY 1,2
ORDER BY 1,2


