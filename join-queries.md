1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT `degrees`.`name` AS `degree_name`, `students.name`, `students.surname`
FROM `students`
INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = "Corso di Laurea in Economia"

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze
SELECT `degrees`.`name`,  `departments`.`name`, `degrees`.`level`
FROM `degrees`
INNER JOIN `departments`
ON `degrees`.`department_id`= `departments`.`id`
WHERE `degrees`.`level` = "magistrale"
AND `departments`.`name`= "Dipartimento di Neuroscienze";


3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT *
FROM `teachers`
INNER JOIN `course_teacher` ON `teachers`.`id`= `course_teacher`.`teacher_id`
INNER JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
WHERE `teachers`.`id`= 44


4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome;
SELECT `students`.`surname`, `students`.`name`, `degrees`.`name` 
FROM `students` 
INNER JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` 
ORDER BY `students`.`surname` ASC;


5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
SELECT `teachers`.`name`, `teachers`.`surname`, `courses`.`name`, `degrees`.`name`
FROM `degrees`
INNER JOIN `courses` ON `degrees`.`id`= `courses`.`degree_id`
INNER JOIN `course_teacher`ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `teachers`ON `teachers`.`id` = `course_teacher`.`teacher_id`

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)
SELECT `teachers`.`name`,`teachers`.`surname`, `departments`.`name` 
FROM `teachers` 
INNER JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` 
INNER JOIN `courses` ON `courses`.`id`= `course_teacher`.`course_id` INNER JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id` 
INNER JOIN `departments`ON `degrees`.`department_id` = `departments`.`id` 
WHERE `departments`.`name`= "Dipartimento di Matematica";

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18

SELECT `students`.`name`, 
		`students`.`surname`, 
        `students`.`id`,
		COUNT(`exam_student`.`student_id`) AS "numero_tentativi",
        MAX(`exam_student`.`vote`) AS "voto_massimo"
        
        
FROM `exam_student`
INNER JOIN `students`ON `students`.`id`= `exam_student`.`student_id`
WHERE `exam_student`.`vote` >= 18
GROUP BY `students`.`id`, `students`.`name`, `students`.`surname`
ORDER BY `students`.`id`, `students`.`name`, `students`.`surname`