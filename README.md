# StudentsMentalHealthData
Project: Analyzing International Students' Mental Health 
---Use my data manipulation skills to explore the data from a study on the mental health of international students, and find out which factors may have the greatest impact.

--View the data 

SELECT *
 FROM `white-resolver-417617.International_students.japan_inter_students ` 
 LIMIT 1000

 --Evaluating international students  
SELECT stay,COUNT(inter_dom) as count_int, 
  ROUND(AVG(todep),2) AS average_phq_depression, 
  ROUND(AVG(tosc),2) AS average_scs_connection, 
  ROUND(AVG(toas),2) AS average_as_stress,
FROM `white-resolver-417617.International_students.japan_inter_students `
WHERE stay IS NOT NULL AND inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC
LIMIT 9;

--Evalutaing domestic students 
SELECT stay,COUNT(inter_dom) as count_int, 
  ROUND(AVG(todep), 2) AS average_phq, 
  ROUND(AVG(tosc), 2) AS average_scs, 
  ROUND(AVG(toas), 2) AS average_as,
FROM `white-resolver-417617.International_students.japan_inter_students `
WHERE stay IS NOT NULL AND inter_dom = 'Dom'
GROUP BY stay
ORDER BY stay DESC
--LIMIT 9;
