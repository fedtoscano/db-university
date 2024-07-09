1. 
SELECT *
FROM `students`
WHERE YEAR(`students`.`date_of_birth`) = 1990;

2. 
SELECT *
FROM `courses`
WHERE `courses`.`cfu` > 10;

3. 
SELECT *
FROM `students`
WHERE 2024 - YEAR(`students`.`date_of_birth`) >= 30;

4.
SELECT * 
FROM `courses`
WHERE `courses`.`period`= "I semestre"
AND `courses`.`year`= 1;

5.
SELECT *
FROM `exams`
WHERE `exams`.`date`= 2020-06-20
AND `exams`.hour > 14;
(non funziona)?

6. 
SELECT *
FROM `degrees`
WHERE `degrees`.`level` = "magistrale"

7.
SELECT COUNT(`id`)
FROM `departments`;

8.
SELECT *
FROM `teachers`
WHERE `teachers`.`phone` IS NULL;