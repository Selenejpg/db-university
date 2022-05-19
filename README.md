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
SELECT * FROM `students` 
JOIN `degrees` ON `students` . `degree_id` = `degrees` . `id` 
WHERE `degrees` . `name` = "Corso di Laurea in Economia"; 


Query 2 

Risposta: 
SELECT * FROM `departments` JOIN `degrees` ON `degrees` . `department_id` || `departments` . `id` WHERE `departments` . `name` = "Dipartimento di Neuroscienze" AND `degrees` . `level` = "magistrale";


Query 3

Risposta: 
SELECT * FROM `teachers`
JOIN `course_teacher` ON `course_teacher` . `teacher_id` = `teachers` . `id`
JOIN `courses` ON `course_teacher` . `course_id` = `courses` . `id`
WHERE `teachers` . `name` = "FULVIO" AND `teachers` . `surname` = "AMATO";


Query 4 

Risposta: 
SELECT * FROM `students`
JOIN `degrees` ON `students` . `degree_id` = `degrees` . `id`
JOIN `departments` ON `departments` . `id` = `degrees` . `department_id`
ORDER BY `students` . `name` ASC, `students` . `surname` ASC;


Query 5

Risposta: 
SELECT *
FROM `degrees` 
JOIN `courses` ON `degrees` . `id` = `courses` . `degree_id`
JOIN `course_teacher` ON `courses` . `id` = `course_teacher` . `course_id`
JOIN `teachers` ON `course_teacher` . `course_id` = `teachers` . `id`;


Query 6

Risposta: 
SELECT *
FROM `teachers`
JOIN `course_teacher` ON `teachers` . `id` = `course_teacher` . `teacher_id`
JOIN `courses` ON `course_teacher` . `course_id` = `course_id`
JOIN `degrees` ON `courses` . `degree_id` = `degree_id`
JOIN `departments` ON `degrees` . `department_id` = `departments` . `id`
WHERE `departments` . `name` = "Dipartimento di Matematica";


Query 7

Risposta: 
SELECT id_studente, SUM(superato), SUM(bocciato)
FROM(SELECT S.id AS id_studente, ES.exam_id AS id_esame, COUNT(*) AS superato, 0 AS bocciato
FROM `students` S
INNER JOIN `exam_student` ES
ON S.id = ES.student_id
WHERE ES.vote >= 18
GROUP BY S.id, ES.exam_id
UNION ALL
SELECT S.id AS id_studente, ES.exam_id AS id_esame,0 AS superato, COUNT(*) AS bocciato
FROM `students` S
INNER JOIN `exam_student` ES ON S.id = ES.student_id
WHERE ES.vote < 18 GROUP BY S.id, ES.exam_id)
GROUP BY id_studente;




