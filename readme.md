Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi **Dipartimenti** (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi Insegnanti;
ogni Corso prevede più appelli d'Esame;
ogni Studente è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

- departments  
   degree programs

- courses  
   teachers

- exam sessions

- students  
   grades

## Table name 'deparments'

**columns**

- id (BIGINT) PK, AUTO_INCREMENT, NOT NULL
- name VARCHAR(255), NOT NULL

## Table name ' degree_programs '

** columns**

- id (BIGINT) PK, AUTO_INCREMENT, NOT NULL
- name VARCHAR(255), NOT NULL
- department_id (BIGINT) FK

## Table name ' courses '

** columns**

- id (BIGINT) PK, AUTO_INCREMENT, NOT NULL
- name VARCHAR(100), NOT NULL
- department_id (BIGINT) FK
- degree_program_id (BIGINT) FK

## Table name ' teachers '

** columns**

- id (BIGINT) PK, AUTO_INCREMENT, NOT NULL
- first_name VARCHAR(255), NOT NULL
- last_name VARCHAR(255), NOT NULL
- email VARCHAR(100), UNIQUE, NOT NULL
- address VARCHAR(255)
- date_of_birthday DATE

## Table name ' course_teacher '

** columns**

- id (BIGINT) PK, AUTO_INCREMENT, NOT NULL
- course_id (BIGINT)
- teacher_id (BIGINT)

## Table name ' exam_sessions '

** columns**

- id (BIGINT) PK, AUTO_INCREMENT, NOT NULL
- course_id (BIGINT) FK → courses(id)
- date DATE, NOT NULL
- location VARCHAR(100)

## Table name ' students '

** columns**

- id (BIGINT) PK, AUTO_INCREMENT, NOT NULL
- first_name VARCHAR(255), NOT NULL
- last_name VARCHAR(255), NOT NULL
- email VARCHAR(100), UNIQUE, NOT NULL
- student_number VARCHAR(20), UNIQUE, NOT NULL
- date_of_birthday DATE
- degree_program_id (BIGINT) FK → degree_programs(id)

## Table name ' grades '

** columns**

- exam_sessions_id (BIGINT) FK → exam_sessions(id)
- student_id (BIGINT) FK → students(id)
- grade TINYINT CHECK (18 ≤ grade ≤ 30)
- PRIMARY KEY (exam_sessions_id, student_id)
