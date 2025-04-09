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

- id (BIGINIT) primary key - auto_increment - NOT NULL
- name VARCHAR(255) - NOT NULL

## Table name ' degree_programs '

** columns**

- id (BIGINIT) primary key - auto_increment - NOT NULL
- name : (VARCHAR (255)) - NOT NULL
- department_id (BIGINIT) - NOT NULL - FOREINGN KEY

## Table name ' courses '

** columns**

- id (BIGINIT) primary key - auto_increment - NOT NULL
- name : (VARCHAR(100)) - NOT NULL
- department_id: (BIGINT) - NOT NULL — FOREIGN KEY
- degree_program_id: (BIGINT) - NOT NULL — FOREIGN KEY

## Table name ' teachers '

** columns**

- id (BIGINIT) primary key - auto_increment - NOT NULL
- first_name (VARCHAR(255)) - NOT NULL
- last_name (VARCHAR(255)) - NOT NULL
- email (VARCHAR(100)) - UNIQUE - NOT NULL
- address (VARCHAR(255))
- date_of_birthday (DATE)

## Table name ' course_teacher '

** columns**

- id (BIGINIT) primary key - auto_increment - NOT NULL
- course_id (BIGINT) - NOT NULL — FOREIGN KEY
- teacher_id (BIGINT) - NOT NULL — FOREIGN KEY

## Table name ' exam_sessions '

** columns**

- id (BIGINIT) primary key - auto_increment - NOT NULL
- course_id (BIGINT) - NOT NULL — FOREIGN KEY
- date (DATE) - NOT NULL
- location (VARCHAR(100))

## Table name ' students '

** columns**

- id (BIGINIT) primary key - auto_increment - NOT NULL
- first_name (VARCHAR(255)) - NOT NULL
- last_name (VARCHAR(255)) - NOT NULL
- email (VARCHAR(100)) - UNIQUE - NOT NULL
- student_number (VARCHAR(20)) - UNIQUE NOT NULL
- date_of_birthday (DATE) (BIGINT) - NOT NULL — FOREIGN KEY
- degree_program_id

## Table name ' grades '

** columns**

- exam_sessions_id (BIGINT) NOT NULL — FOREIGN KEY
- student_id (BIGINT) NOT NULL — FOREIGN KEY
- grade (TINYINT) — from 18 to 30
