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
FROM `course_teacher`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `teachers`.`name` = "Fulvio"
AND `teachers`.`surname` = "Amato"

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
