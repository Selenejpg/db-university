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



