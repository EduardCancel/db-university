📌 JOIN

/\* Join

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

- degrees
- students

SELECT \*
FROM `students`
JOIN `degrees`ON `students`.`degree_id`= `degrees`.`id`
WHERE `degrees`.`name`= 'Corso di Laurea in Economia'

\*/

/\* 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

- courses
- degrees
- departments

SELECT \*
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id`= `departments`.`id`
WHERE `departments`.`name`= 'Dipartimento di Neuroscienza' AND `degrees`.`level`= 'magistrale'

\*/

/\* 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

-course_teacher
-courses
-teachers

SELECT \*
FROM teachers
JOIN course_teacher ON course_teacher.teacher_id = teachers.id
JOIN courses ON course_teacher.course_id = courses.id
WHERE teachers.id = 44;

\*/

/\* 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

- students
- degrees
- departments

SELECT \*
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname`, `students`.`name`

\*/

/\* 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

-degrees
-teachers
-course
-course_teacher

SELECT \*
FROM `course_teacher`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`

\*/

/\*

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

-course_teacher
-teachers
-courses
-degrees
-departments

SELECT \*
FROM `course_teacher`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = "Dipartimento di Matematica"

\*/

📌 GROUP BY

/\*

1. Contare quanti iscritti ci sono stati ogni anno

SELECT YEAR(`enrolment_date`) AS `year`, COUNT(\*) AS `number_students`
FROM `students`
GROUP BY `year`;

\*/

/\*

2.  Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT `office_address`, COUNT(_)
FROM `teachers`
GROUP BY `office_address`
_/

/\*

3. Calcolare la media dei voti di ogni appello d'esame

SELECT AVG(`exam_student`.`vote`) AS `vote_average`, `courses`.`name` AS `course_name`, `degrees`.`name` AS `degree_name`
FROM `exam_student`
JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id`
JOIN `courses` ON `exams`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
GROUP BY `courses`.`id`
ORDER BY `vote_average` DESC

\*/

/\*

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT `departments`.`name`, COUNT(\*)
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
GROUP BY `departments`.`name`

\*/
