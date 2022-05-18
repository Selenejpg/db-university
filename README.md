Query 1

Risposta: (160)
SELECT * FROM `students` WHERE YEAR(`date_of_birth`) = '1990';


Query 2

Risposta: (479)
SELECT * FROM `courses` WHERE `cfu` > 10;


Query 3

Risposta: (3237)
SELECT * FROM `students` WHERE TIMESTAMPDIFF(YEAR,`date_of_birth`,CURDATE()) > 30;


Query 4 

Risposta: (286)
SELECT * FROM `courses` WHERE `period` = 'I semestre' AND `year` = '1';


Query 5

Risposta: (21)
SELECT * FROM `exams` WHERE `date` = '2020-06-20' AND `hour` > '14:00:00';


Query 6

Risposta: (38)
SELECT * FROM `degrees` WHERE `level` = 'magistrale';


Query 7

Risposta: (12)
SELECT * FROM `departments`;
SELECT COUNT(*) AS `departments` FROM `departments`;


Query 8

Risposta: (50)
SELECT * FROM `teachers` WHERE IsNull(`phone`);
SELECT COUNT(*) AS `teachers` FROM `teachers` WHERE IsNull(`phone`);


QUERY CON GROUP BY

Query 1

Risposta:
SELECT COUNT(id), YEAR(`enrolment_date`) FROM `students` WHERE `enrolment_date` GROUP BY YEAR(`enrolment_date`);


Query 2

Risposta: 
SELECT COUNT(id), `office_address` FROM `teachers` GROUP BY `office_address`;


Query 3

Risposta: 
SELECT AVG(`vote`) 'Media dei voti', `exam_id`  FROM `exam_student` GROUP BY `exam_id`;


Query 4 

Risposta: 
SELECT COUNT(`name`), `department_id` FROM `degrees` GROUP BY `department_id`;


QUERY CON JOIN

Query 1

Risposta: 

Query 2

Risposta: 


Query 3

Risposta: 


Query 4 

Risposta: 


Query 5

Risposta: 


Query 6

Risposta: 


Query 7

Risposta: 



