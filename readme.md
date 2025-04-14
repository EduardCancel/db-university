Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi **Dipartimenti** (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi Insegnanti;
ogni Corso prevede più appelli d'Esame;
ogni Studente è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

## Tables

- departments
- degrees
- courses
- teachers
- exams
- students

## Table: departments

- id: INT PK AI NN UN
- name: VARCHAR(100) NOT NULL
- head_of_department: VARCHAR(100) NOT NULL
- phone_number: CHAR(100) NULL
- email: VARCHAR(150)

## Table: degrees ( departments -> degreese)

- id: INT PK AI NN UN
- name: VARCHAR(100) NOT NULL
- department_id : INIT FK
- level
- website

## Table: courses

- id: INT PK AI NN UN
- name: VARCHAR(100) NOT NULL
- degree_id : INT UN
- cfu: TINYINIT
- period: VARCHAR(50) NULL
- email: VARCHAR(150)

## Table: teachers

- id: INT PK AI NN UN
- name: VARCHAR(100) NOT NULL
- lastname: VARCHAR(100) NOT NULL
- phone_number: CHAR(100) NULL
- email: VARCHAR(150)

## Table: exams

- id: INT PK AI NN UN
- course_id: INT (FK)
- date: DATE NOT NULL
- hour: TIME NOT NULL
- location: VARCHAR(100) NOT NULL
- address: VARCHAR(100) NOT NULL

## Table: students

- id: INT PK AI NN UN
- degree_id: FK
- phone_number: CHAR(100) NULL
- email: VARCHAR(150)
