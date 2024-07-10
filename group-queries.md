1. Contare quanti iscritti ci sono stati ogni anno

SELECT YEAR(`students`.`enrolment_date`) AS enrolment_year, COUNT(*) AS student_count
FROM `students`
GROUP BY YEAR(`students`.`enrolment_date`);


2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT `office_address`, COUNT(`office_address`) AS `teacher_addresses`
FROM `teachers`
GROUP BY `office_address`;

3. Calcolare la media dei voti di ogni appello d'esame
SELECT AVG(`exam_student`.`vote`) as `votazione_media`, `exam_id`
FROM `exam_student`
GROUP BY `exam_id`

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT COUNT(`id`) AS `lista_corsi`, `degrees`.`department_id`
FROM `degrees`
GROUP BY `degrees`.`department_id`
