# postgres_sql
``` bash
Microsoft Windows [Version 10.0.26100.4061]
(c) Microsoft Corporation. All rights reserved.

C:\Program Files\PostgreSQL\17\bin>psql -U Nithin -d university_db
Password for user Nithin:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "Nithin"

C:\Program Files\PostgreSQL\17\bin>psql -U Nithin -d university_db
Password for user Nithin:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "Nithin"

C:\Program Files\PostgreSQL\17\bin>psql -U Nithin -d university_db;
Password for user Nithin:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "Nithin"

C:\Program Files\PostgreSQL\17\bin>psql -U Nithin -d university_db;
Password for user Nithin:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "Nithin"

C:\Program Files\PostgreSQL\17\bin>psql -U postgres -d postgres
Password for user postgres:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "postgres"

C:\Program Files\PostgreSQL\17\bin>psql -U postgres -d postgres
Password for user postgres:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "postgres"

C:\Program Files\PostgreSQL\17\bin>psql -U postgres -d postgres
Password for user postgres:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

postgres=# \du
                             List of roles
 Role name |                         Attributes
-----------+------------------------------------------------------------
 nithin    |
 postgres  | Superuser, Create role, Create DB, Replication, Bypass RLS


postgres=# ALTER USER Nithin WITH PASSWORD 'Nithin@6';
ALTER ROLE
postgres=# GRANT CONNECT ON DATABASE university_db TO Nithin;
GRANT
postgres=# \q

C:\Program Files\PostgreSQL\17\bin>psql -U Nithin -d university_db
Password for user Nithin:

psql: error: connection to server at "localhost" (::1), port 5432 failed: FATAL:  password authentication failed for user "Nithin"

C:\Program Files\PostgreSQL\17\bin>psql -U nithin -d university_db
Password for user nithin:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

university_db=> \du
                             List of roles
 Role name |                         Attributes
-----------+------------------------------------------------------------
 nithin    |
 postgres  | Superuser, Create role, Create DB, Replication, Bypass RLS


university_db=> GRANT ALL ON DATABASE university_db TO nithin;
GRANT
university_db=> CREATE TABLE students (
university_db(>     student_id INTEGER,
university_db(>     first_name VARCHAR(50),
university_db(>     last_name VARCHAR(50),
university_db(>     email VARCHAR(100),
university_db(>     date_of_birth DATE
university_db(> );
CREATE TABLE
university_db=> CREATE TABLE students(
university_db(>
university_db(> show students
university_db(> select * from students
university_db(> SELECT * FROM students;
university_db(> \d
         List of relations
 Schema |   Name   | Type  | Owner
--------+----------+-------+--------
 public | students | table | nithin
(1 row)


university_db(> ALTER TABLE students ADD COLUMN enrollment_date DATE;
university_db(> ALTER TABLE students ADD COLUMN enrollment_date DATE;
university_db(> \q

C:\Program Files\PostgreSQL\17\bin>psql -U nithin -d university_db
Password for user nithin:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

university_db=> ALTER TABLE students ADD COLUMN enrollment_date DATE;
ALTER TABLE
university_db=> ALTER TABLE students DROP COLUMN enrollment_date;
ALTER TABLE
university_db=> ALTER TABLE students ALTER COLUMN email TYPE VARCHAR(150);
ALTER TABLE
university_db=> ALTER TABLE students RENAME COLUMN date_of_birth TO dob;
ALTER TABLE
university_db=> ALTER TABLE students ADD CONSTRAINT unique_email UNIQUE (email);
ALTER TABLE
university_db=> ALTER TABLE students ADD COLUMN phone_number VARCHAR(20);
ALTER TABLE
university_db=> ALTER TABLE students DROP COLUMN phone_number;
ALTER TABLE
university_db=> INSERT INTO students (student_id,fisrt_name,last_name,dob)
university_db-> VALUES (1, 'Siva', 'Nithin', 'siva.nithin@example.com', '2003-05-15');
ERROR:  column "fisrt_name" of relation "students" does not exist
LINE 1: INSERT INTO students (student_id,fisrt_name,last_name,dob)
                                         ^
university_db=> INSERT INTO students (student_id,fisrt_name,last_name,dob)
university_db-> VALUES (1, 'Siva', 'Nithin', 'siva.nithin@example.com', '2003-05-15');
ERROR:  column "fisrt_name" of relation "students" does not exist
LINE 1: INSERT INTO students (student_id,fisrt_name,last_name,dob)
                                         ^
university_db=> INSERT INTO students (student_id,first_name,last_name,dob)
university_db-> VALUES (1, 'Siva', 'Nithin', 'siva.nithin@example.com', '2003-05-15');
ERROR:  INSERT has more expressions than target columns
LINE 2: ... (1, 'Siva', 'Nithin', 'siva.nithin@example.com', '2003-05-1...
                                                             ^
university_db=> INSERT INTO students (student_id,fisrt_name,last_name,dob)
university_db-> VALUES (1, 'Siva', 'Nithin', 'siva.nithin@example.com', '2003-05-15');
ERROR:  column "fisrt_name" of relation "students" does not exist
LINE 1: INSERT INTO students (student_id,fisrt_name,last_name,dob)
                                         ^
university_db=> INSERT INTO students (student_id,fisrt_name,last_name,email,dob)
university_db-> VALUES (1, 'Siva', 'Nithin', 'siva.nithin@example.com', '2003-05-15');
ERROR:  column "fisrt_name" of relation "students" does not exist
LINE 1: INSERT INTO students (student_id,fisrt_name,last_name,email,...
                                         ^
university_db=> INSERT INTO students (student_id,first_name,last_name,email,dob)
university_db-> VALUES (1, 'Siva', 'Nithin', 'siva.nithin@example.com', '2003-05-15');
INSERT 0 1
university_db=> INSERT INTO students (student_id, first_name, last_name, email, dob)
university_db-> VALUES (2, 'Bob', 'Johnson', 'bob.johnson@example.com', '2002-08-22'),
university_db->        (3, 'Charlie', 'Brown', 'charlie.brown@example.com', '2003-01-10');
INSERT 0 2
university_db=> INSERT INTO students (student_id, first_name, last_name, email, dob)
university_db-> VALUES (4, 'Aravind', 'Mandan', 'aravindh.mandan@example.com', '2003-05-11');
INSERT 0 1
university_db=> INSERT INTO students (student_id, first_name, last_name, email, dob)
university_db-> VALUES (5, 'Nihar', 'Edula', 'nihar.edula@example.com', '2003-08-11');
INSERT 0 1
university_db=> SELECT * From students where first_name='Alice';
 student_id | first_name | last_name | email | dob
------------+------------+-----------+-------+-----
(0 rows)


university_db=> SELECT * From students where first_name='Siva';
 student_id | first_name | last_name |          email          |    dob
------------+------------+-----------+-------------------------+------------
          1 | Siva       | Nithin    | siva.nithin@example.com | 2003-05-15
(1 row)


university_db=> SELECT * From students
university_db-> SELECT * From students ;
ERROR:  syntax error at or near "SELECT"
LINE 2: SELECT * From students ;
        ^
university_db=> SELECT * From students ;
 student_id | first_name | last_name |            email            |    dob
------------+------------+-----------+-----------------------------+------------
          1 | Siva       | Nithin    | siva.nithin@example.com     | 2003-05-15
          2 | Bob        | Johnson   | bob.johnson@example.com     | 2002-08-22
          3 | Charlie    | Brown     | charlie.brown@example.com   | 2003-01-10
          4 | Aravind    | Mandan    | aravindh.mandan@example.com | 2003-05-11
          5 | Nihar      | Edula     | nihar.edula@example.com     | 2003-08-11
(5 rows)


university_db=> SELECT * From students where student_id=1;
 student_id | first_name | last_name |          email          |    dob
------------+------------+-----------+-------------------------+------------
          1 | Siva       | Nithin    | siva.nithin@example.com | 2003-05-15
(1 row)


university_db=> SELECT * From students where dob > '2003-05-15';
 student_id | first_name | last_name |          email          |    dob
------------+------------+-----------+-------------------------+------------
          5 | Nihar      | Edula     | nihar.edula@example.com | 2003-08-11
(1 row)


university_db=> SELECT* FROM studnets where first_name LIKE A%;
ERROR:  syntax error at or near ";"
LINE 1: SELECT* FROM studnets where first_name LIKE A%;
                                                      ^
university_db=> SELECT* FROM studnets where first_name LIKE 'A%';
ERROR:  relation "studnets" does not exist
LINE 1: SELECT* FROM studnets where first_name LIKE 'A%';
                     ^
university_db=> SELECT* FROM students where first_name LIKE 'A%';
 student_id | first_name | last_name |            email            |    dob
------------+------------+-----------+-----------------------------+------------
          4 | Aravind    | Mandan    | aravindh.mandan@example.com | 2003-05-11
(1 row)


university_db=> SELECT * FROM students WHERE student_id IN=1, 3, 5 ;
ERROR:  syntax error at or near "="
LINE 1: SELECT * FROM students WHERE student_id IN=1, 3, 5 ;
                                                  ^
university_db=> SELECT * FROM students WHERE student_id IN(1, 3, 5) ;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+------------
          1 | Siva       | Nithin    | siva.nithin@example.com   | 2003-05-15
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-10
          5 | Nihar      | Edula     | nihar.edula@example.com   | 2003-08-11
(3 rows)


university_db=> SELECT * FROM studnets where student_id=2;
ERROR:  relation "studnets" does not exist
LINE 1: SELECT * FROM studnets where student_id=2;
                      ^
university_db=> SELECT * FROM students where student_id=2;
 student_id | first_name | last_name |          email          |    dob
------------+------------+-----------+-------------------------+------------
          2 | Bob        | Johnson   | bob.johnson@example.com | 2002-08-22
(1 row)


university_db=> SELECT * FROM students where dob>2003-01-01;
ERROR:  operator does not exist: date > integer
LINE 1: SELECT * FROM students where dob>2003-01-01;
                                        ^
HINT:  No operator matches the given name and argument types. You might need to add explicit type casts.
university_db=> SELECT * FROM students where dob>'2003-01-01';
 student_id | first_name | last_name |            email            |    dob
------------+------------+-----------+-----------------------------+------------
          1 | Siva       | Nithin    | siva.nithin@example.com     | 2003-05-15
          3 | Charlie    | Brown     | charlie.brown@example.com   | 2003-01-10
          4 | Aravind    | Mandan    | aravindh.mandan@example.com | 2003-05-11
          5 | Nihar      | Edula     | nihar.edula@example.com     | 2003-08-11
(4 rows)


university_db=> SELECT * FROM students where dob<'2003-01-01';
 student_id | first_name | last_name |          email          |    dob
------------+------------+-----------+-------------------------+------------
          2 | Bob        | Johnson   | bob.johnson@example.com | 2002-08-22
(1 row)


university_db=> SELECT * FROM students where first_name LIKE 'B%' AND 'C%';
ERROR:  invalid input syntax for type boolean: "C%"
LINE 1: SELECT * FROM students where first_name LIKE 'B%' AND 'C%';
                                                              ^
university_db=> SELECT * FROM students where first_name LIKE 'B%' ;
 student_id | first_name | last_name |          email          |    dob
------------+------------+-----------+-------------------------+------------
          2 | Bob        | Johnson   | bob.johnson@example.com | 2002-08-22
(1 row)


university_db=> SELECT * FROM students where first_name LIKE 'B%' OR 'C%' ;
ERROR:  invalid input syntax for type boolean: "C%"
LINE 1: SELECT * FROM students where first_name LIKE 'B%' OR 'C%' ;
                                                             ^
university_db=> SELECT * FROM students where first_name LIKE 'B%' OR  LIKE 'C%' ;
ERROR:  type "like" does not exist
LINE 1: ...CT * FROM students where first_name LIKE 'B%' OR  LIKE 'C%' ...
                                                             ^
university_db=> SELECT * FROM students where first_name LIKE 'B%' OR   first_name LIKE 'C%' ;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+------------
          2 | Bob        | Johnson   | bob.johnson@example.com   | 2002-08-22
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-10
(2 rows)


university_db=> SELECT * FROM students where email LIKE '%email.com';
 student_id | first_name | last_name | email | dob
------------+------------+-----------+-------+-----
(0 rows)


university_db=> SELECT * FROM students where email LIKE '%example.com';
 student_id | first_name | last_name |            email            |    dob
------------+------------+-----------+-----------------------------+------------
          1 | Siva       | Nithin    | siva.nithin@example.com     | 2003-05-15
          2 | Bob        | Johnson   | bob.johnson@example.com     | 2002-08-22
          3 | Charlie    | Brown     | charlie.brown@example.com   | 2003-01-10
          4 | Aravind    | Mandan    | aravindh.mandan@example.com | 2003-05-11
          5 | Nihar      | Edula     | nihar.edula@example.com     | 2003-08-11
(5 rows)


university_db=> SELECT * FROM students where email=ISNUL;
ERROR:  column "isnul" does not exist
LINE 1: SELECT * FROM students where email=ISNUL;
                                           ^
university_db=> SELECT * FROM students where email=NULL;
 student_id | first_name | last_name | email | dob
------------+------------+-----------+-------+-----
(0 rows)


university_db=> UPDATE students
university_db-> SET first_name = 'Robert', email = 'robert.j@example.com'
university_db->
university_db-> UPDATE students
university_db->
university_db-> ;
ERROR:  syntax error at or near "UPDATE"
LINE 3: UPDATE students
        ^
university_db=> Select * from students order by last_name  ASC AND order by first_name DESC
university_db-> Select * from students order by last_name  ASC AND order by first_name DESC;
ERROR:  syntax error at or near "AND"
LINE 1: Select * from students order by last_name  ASC AND order by ...
                                                       ^
university_db=> Select * from students  order by last_name ASC,first_name DESC;
 student_id | first_name | last_name |            email            |    dob
------------+------------+-----------+-----------------------------+------------
          3 | Charlie    | Brown     | charlie.brown@example.com   | 2003-01-10
          5 | Nihar      | Edula     | nihar.edula@example.com     | 2003-08-11
          2 | Bob        | Johnson   | bob.johnson@example.com     | 2002-08-22
          4 | Aravind    | Mandan    | aravindh.mandan@example.com | 2003-05-11
          1 | Siva       | Nithin    | siva.nithin@example.com     | 2003-05-15
(5 rows)


university_db=> SELECT * FROM students ORDER BY student_id LIMIT 2 OFFSET 2;
 student_id | first_name | last_name |            email            |    dob
------------+------------+-----------+-----------------------------+------------
          3 | Charlie    | Brown     | charlie.brown@example.com   | 2003-01-10
          4 | Aravind    | Mandan    | aravindh.mandan@example.com | 2003-05-11
(2 rows)


university_db=> SELECT * FROM students ORDER BY dob ASC LIMIT 1;
 student_id | first_name | last_name |          email          |    dob
------------+------------+-----------+-------------------------+------------
          2 | Bob        | Johnson   | bob.johnson@example.com | 2002-08-22
(1 row)


university_db=> SELECT * FROM students ORDER BY student_id offset 1 limit 2
university_db-> SELECT * FROM students ORDER BY student_id offset 1 limit 2;
ERROR:  syntax error at or near "SELECT"
LINE 2: SELECT * FROM students ORDER BY student_id offset 1 limit 2;
        ^
university_db=> SELECT * FROM students ORDER BY student_id limit 2 offset 1;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+------------
          2 | Bob        | Johnson   | bob.johnson@example.com   | 2002-08-22
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-10
(2 rows)


university_db=>
university_db=> SELECT * FROM students ORDER BY student_id LIMIT 2 OFFSET 2;
 student_id | first_name | last_name |            email            |    dob
------------+------------+-----------+-----------------------------+------------
          3 | Charlie    | Brown     | charlie.brown@example.com   | 2003-01-10
          4 | Aravind    | Mandan    | aravindh.mandan@example.com | 2003-05-11
(2 rows)


university_db=> SELECT * FROM students ORDER BY dob ASC LIMIT 1;
 student_id | first_name | last_name |          email          |    dob
------------+------------+-----------+-------------------------+------------
          2 | Bob        | Johnson   | bob.johnson@example.com | 2002-08-22
(1 row)


university_db=> SELECT * FROM students ORDER BY student_id offset 1 limit 2
university_db-> SELECT * FROM students ORDER BY student_id offset 1 limit 2;
ERROR:  syntax error at or near "SELECT"
LINE 2: SELECT * FROM students ORDER BY student_id offset 1 limit 2;
        ^
university_db=> SELECT * FROM students ORDER BY student_id limit 2 offset 1;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+------------
          2 | Bob        | Johnson   | bob.johnson@example.com   | 2002-08-22
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-10
(2 rows)


university_db=> select * from students;
 student_id | first_name | last_name |            email            |    dob
------------+------------+-----------+-----------------------------+------------
          1 | Siva       | Nithin    | siva.nithin@example.com     | 2003-05-15
          2 | Bob        | Johnson   | bob.johnson@example.com     | 2002-08-22
          3 | Charlie    | Brown     | charlie.brown@example.com   | 2003-01-10
          4 | Aravind    | Mandan    | aravindh.mandan@example.com | 2003-05-11
          5 | Nihar      | Edula     | nihar.edula@example.com     | 2003-08-11
(5 rows)


university_db=> INSERT INTO students (student_id, first_name, last_name, email, dob)
university_db-> VALUES (5, 'Eve', 'Smith', 'eve.smith@example.com', '2004-07-01');
INSERT 0 1
university_db=> select * from students;
 student_id | first_name | last_name |            email            |    dob
------------+------------+-----------+-----------------------------+------------
          1 | Siva       | Nithin    | siva.nithin@example.com     | 2003-05-15
          2 | Bob        | Johnson   | bob.johnson@example.com     | 2002-08-22
          3 | Charlie    | Brown     | charlie.brown@example.com   | 2003-01-10
          4 | Aravind    | Mandan    | aravindh.mandan@example.com | 2003-05-11
          5 | Nihar      | Edula     | nihar.edula@example.com     | 2003-08-11
          5 | Eve        | Smith     | eve.smith@example.com       | 2004-07-01
(6 rows)


university_db=> UPDATE TABLE students
university_db-> SET student_id=6  AND last_name='Brown'
university_db-> WHERE first_name = 'Eve' ;
ERROR:  syntax error at or near "TABLE"
LINE 1: UPDATE TABLE students
               ^
university_db=> UPDATE students
university_db-> SET student_id=6  AND last_name='Brown'
university_db-> WHERE first_name = 'Eve' ;
ERROR:  argument of AND must be type boolean, not type integer
LINE 2: SET student_id=6  AND last_name='Brown'
                       ^
university_db=> UPDATE students
university_db-> SET student_id = 6, last_name = 'Brown'
university_db-> WHERE first_name = 'Eve';
UPDATE 1
university_db=> select * from students;
 student_id | first_name | last_name |            email            |    dob
------------+------------+-----------+-----------------------------+------------
          1 | Siva       | Nithin    | siva.nithin@example.com     | 2003-05-15
          2 | Bob        | Johnson   | bob.johnson@example.com     | 2002-08-22
          3 | Charlie    | Brown     | charlie.brown@example.com   | 2003-01-10
          4 | Aravind    | Mandan    | aravindh.mandan@example.com | 2003-05-11
          5 | Nihar      | Edula     | nihar.edula@example.com     | 2003-08-11
          6 | Eve        | Brown     | eve.smith@example.com       | 2004-07-01
(6 rows)


university_db=> SELECT last_name FROM students;
 last_name
-----------
 Nithin
 Johnson
 Brown
 Mandan
 Edula
 Brown
(6 rows)


university_db=> SELECT DISTINCT last_name FROM students ORDER BY last_name;
 last_name
-----------
 Brown
 Edula
 Johnson
 Mandan
 Nithin
(5 rows)


university_db=> SELECT DISTINCT last_name, first_name FROM students;
 last_name | first_name
-----------+------------
 Brown     | Eve
 Mandan    | Aravind
 Nithin    | Siva
 Edula     | Nihar
 Brown     | Charlie
 Johnson   | Bob
(6 rows)


university_db=> SELECT DISTINCT date_of_birth
university_db-> FROM students
university_db-> ORDER BY date_of_birth;
ERROR:  column "date_of_birth" does not exist
LINE 1: SELECT DISTINCT date_of_birth
                        ^
university_db=> SELECT DISTINCT dob
university_db-> FROM students
university_db-> ORDER BY dob;
    dob
------------
 2002-08-22
 2003-01-10
 2003-05-11
 2003-05-15
 2003-08-11
 2004-07-01
(6 rows)


university_db=> SELECT DISTINCT EXTRACT(YEAR FROM dob) AS birth_year
university_db-> FROM students
university_db-> ORDER BY birth_year;
 birth_year
------------
       2002
       2003
       2004
(3 rows)


university_db=> SELECT COUNT(*) AS total_students FROM students;
 total_students
----------------
              6
(1 row)


university_db=> SELECT MIN(dob) AS oldest_student_dob FROM students;
 oldest_student_dob
--------------------
 2002-08-22
(1 row)


university_db=> SELECT first_name ,MIN(dob) AS oldest_student_dob FROM students;
ERROR:  column "students.first_name" must appear in the GROUP BY clause or be used in an aggregate function
LINE 1: SELECT first_name ,MIN(dob) AS oldest_student_dob FROM stude...
               ^
university_db=> SELECT first_name form students MIN(dob) AS oldest_student_dob FROM students;
ERROR:  syntax error at or near "students"
LINE 1: SELECT first_name form students MIN(dob) AS oldest_student_d...
                               ^
university_db=> SELECT MIN(dob) AS oldest_student_dob FROM students;
 oldest_student_dob
--------------------
 2002-08-22
(1 row)


university_db=> SELCT * FROM students
university_db-> where oldest_student_job=MIN(dob) ;
ERROR:  syntax error at or near "SELCT"
LINE 1: SELCT * FROM students
        ^
university_db=> SELECT * FROM students
university_db-> WHERE dob = (SELECT MIN(dob) FROM students);
 student_id | first_name | last_name |          email          |    dob
------------+------------+-----------+-------------------------+------------
          2 | Bob        | Johnson   | bob.johnson@example.com | 2002-08-22
(1 row)


university_db=> SELECT COUNT(DISTINCT last_name) AS unique_last_names FROM students;
 unique_last_names
-------------------
                 5
(1 row)


university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=>
university_db=> SELECT first_name, COUNT(*) AS student_count
university_db-> FROM students
university_db-> GROUP BY first_name;
 first_name | student_count
------------+---------------
 Nihar      |             1
 Aravind    |             1
 Siva       |             1
 Eve        |             1
 Bob        |             1
 Charlie    |             1
(6 rows)


university_db=> select dob count(*) as years
university_db-> from students
university_db-> GROUP BY dob;
ERROR:  syntax error at or near "("
LINE 1: select dob count(*) as years
                        ^
university_db=> select dob, count(*) as years
university_db-> from students
university_db-> GROUP BY dob;
    dob     | years
------------+-------
 2003-05-11 |     1
 2002-08-22 |     1
 2003-05-15 |     1
 2003-08-11 |     1
 2003-01-10 |     1
 2004-07-01 |     1
(6 rows)


university_db=> SELECT EXTRACT(YEAR FROM dob) AS birth_year, COUNT(*) AS students_in_year
university_db-> FROM students
university_db-> WHERE dob IS NOT NULL
university_db-> GROUP BY birth_year
university_db-> ORDER BY birth_year;
 birth_year | students_in_year
------------+------------------
       2002 |                1
       2003 |                4
       2004 |                1
(3 rows)


university_db=> SELECT YEAR(dob) AS birth_year, COUNT(*) AS student_count
university_db-> FROM students
university_db-> GROUP BY YEAR(dob);
ERROR:  function year(date) does not exist
LINE 1: SELECT YEAR(dob) AS birth_year, COUNT(*) AS student_count
               ^
HINT:  No function matches the given name and argument types. You might need to add explicit type casts.
university_db=>


university_db=>
university_db=> DROP TABLE students;
DROP TABLE
university_db=> select (*) from students;
ERROR:  syntax error at or near "*"
LINE 1: select (*) from students;
                ^
university_db=> select * from students;
ERROR:  relation "students" does not exist
LINE 1: select * from students;
                      ^
university_db=> create table students
university_db-> create table students(
university_db(> student_id SERIAL PRIMARY KEY,
university_db(> ;
university_db(>
university_db(> ;
university_db(> \q

C:\Program Files\PostgreSQL\17\bin>psql -U nithin -d university_db
Password for user nithin:

psql (17.5)
WARNING: Console code page (437) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

university_db=> create table students(
university_db(> student_id serial primary key,
university_db(> first_name VARCHAR(50) NOT NULL,
university_db(> last_name VARCHAR(50) NOT NULL,
university_db(> email VARCHAR(100) UNIQUE,
university_db(> dob DATE,
university_db(> enrollment_status VARCHAR(20) CHECK (enrollment_status IN ('enrolled', 'graduated', 'dropped', 'pending'))
university_db(> );
CREATE TABLE
university_db=> select * from students;
 student_id | first_name | last_name | email | dob | enrollment_status
------------+------------+-----------+-------+-----+-------------------
(0 rows)


university_db=> -- Insert data (student_id will be auto-generated)
university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> INSERT INTO students (first_name, last_name, email, dob, enrollment_status);
ERROR:  syntax error at or near "INSERT"
LINE 2: INSERT INTO students (first_name, last_name, email, dob, enr...
        ^
university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES (NULL, 'Smith', 'alice.smith@example.com', '2003-05-15', 'enrolled');
ERROR:  null value in column "first_name" of relation "students" violates not-null constraint
DETAIL:  Failing row contains (1, null, Smith, alice.smith@example.com, 2003-05-15, enrolled).
university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Alice', 'Smith', 'alice.smith@example.com', '2003-05-15', 'enrolled');
INSERT 0 1
university_db=> select * from students;
 student_id | first_name | last_name |          email          |    dob     | enrollment_status
------------+------------+-----------+-------------------------+------------+-------------------
          2 | Alice      | Smith     | alice.smith@example.com | 2003-05-15 | enrolled
(1 row)


university_db=> DROP table students;
DROP TABLE
university_db=> CREATE TABLE students (
university_db(>     student_id SERIAL PRIMARY KEY,  -- student_id is now PK, auto-incrementing, NOT NULL
university_db(>     first_name VARCHAR(50) NOT NULL,
university_db(>     last_name VARCHAR(50) NOT NULL,
university_db(>     email VARCHAR(100) UNIQUE,      -- Email should be unique; can be NULL unless NOT NULL is added
university_db(>     dob DATE,
university_db(>     enrollment_status VARCHAR(20) CHECK (enrollment_status IN ('enrolled', 'graduated', 'dropped', 'pending'))
university_db(> hkjn;
university_db(> ;
university_db(> );
ERROR:  syntax error at or near "hkjn"
LINE 8: hkjn;
        ^
university_db=> CREATE TABLE students (
university_db(>     student_id SERIAL PRIMARY KEY,      first_name VARCHAR(50) NOT NULL,
university_db(>     last_name VARCHAR(50) NOT NULL,
university_db(>     email VARCHAR(100) UNIQUE,          dob DATE,
university_db(>     enrollment_status VARCHAR(20) CHECK (enrollment_status IN ('enrolled', 'graduated', 'dropped', 'pending'))
university_db(> );
CREATE TABLE
university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Steve', 'Smith', 'steve.smith@example.com', '2003-05-15', 'enrolled');
INSERT 0 1
university_db=> select * from students;
 student_id | first_name | last_name |          email          |    dob     | enrollment_status
------------+------------+-----------+-------------------------+------------+-------------------
          1 | Steve      | Smith     | steve.smith@example.com | 2003-05-15 | enrolled
(1 row)


university_db=> CREATE TABLE courses (
university_db(>     course_id SERIAL PRIMRY KEY,
university_db(>     course_name VARCHAR(100) NOT NULL UNIQUE,
university_db(>     credits INTEGER CHECK (credits > 0 AND credits < 10) );
ERROR:  syntax error at or near "PRIMRY"
LINE 2:     course_id SERIAL PRIMRY KEY,
                             ^
university_db=> CREATE TABLE courses (
university_db(>     course_id SERIAL PRIMARY KEY,
university_db(>     course_name VARCHAR(100) NOT NULL UNIQUE,
university_db(>     credits INTEGER CHECK (credits > 0 AND credits < 10) );
CREATE TABLE
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Introduction to SQL', 3);
INSERT 0 1
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Database Design', 4);
INSERT 0 1
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Web Development', 3);
INSERT 0 1
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Data Structures', 4);
INSERT 0 1
university_db=> CREATE TABLE enrollments (
university_db(>     enrollment_id SERIAL PRIMARY KEY,
university_db(>     student_id INTEGER NOT NULL,
university_db(>     course_id INTEGER NOT NULL,
university_db(>     enrollment_date DATE DEFAULT CURRENT_DATE, -- Sets default if not specified
university_db(>     grade CHAR(1) CHECK (grade IN ('A', 'B', 'C', 'D', 'F', 'W', NULL)), -- W for withdraw, NULL if not graded
university_db(>
university_db(>     -- Foreign Key constraint for student_id
university_db(>     CONSTRAINT fk_student
university_db(>         FOREIGN KEY (student_id)
university_db(>         REFERENCES students(student_id)
university_db(>         ON DELETE CASCADE, -- If a student is deleted, their enrollments are also deleted.
university_db(>                            -- Other options: ON DELETE RESTRICT, ON DELETE SET NULL, ON DELETE SET DEFAULT
university_db(>
university_db(>     -- Foreign Key constraint for course_id
university_db(>     CONSTRAINT fk_course
university_db(>         FOREIGN KEY (course_id)
university_db(>         REFERENCES courses(course_id)
university_db(>         ON DELETE RESTRICT, -- (Default if not specified) Prevent deleting a course if students are enrolled.
university_db(>
university_db(>     -- Ensure a student cannot enroll in the same course multiple times (if semester isn't a factor)
university_db(>     UNIQUE (student_id, course_id)
university_db(> );
CREATE TABLE
university_db=> Select * from course;
ERROR:  relation "course" does not exist
LINE 1: Select * from course;
                      ^
university_db=> Select * from courses
university_db-> ;
 course_id |     course_name     | credits
-----------+---------------------+---------
         1 | Introduction to SQL |       3
         2 | Database Design     |       4
         3 | Web Development     |       3
         4 | Data Structures     |       4
(4 rows)


university_db=> INSERT INTO enrollments (student_id, course_id, grade) VALUES (1, 1, 'A');
INSERT 0 1
university_db=> INSERT INTO enrollments (student_id, course_id) VALUES (1, 2);
INSERT 0 1
university_db=> INSERT INTO enrollments (student_id, course_id, grade) VALUES (2, 1, 'B');
ERROR:  insert or update on table "enrollments" violates foreign key constraint "fk_student"
DETAIL:  Key (student_id)=(2) is not present in table "students".
university_db=> select * from enrollments;
 enrollment_id | student_id | course_id | enrollment_date | grade
---------------+------------+-----------+-----------------+-------
             1 |          1 |         1 | 2025-05-30      | A
             2 |          1 |         2 | 2025-05-30      |
(2 rows)


university_db=> SELECT * FROM students;
 student_id | first_name | last_name |          email          |    dob     | enrollment_status
------------+------------+-----------+-------------------------+------------+-------------------
          1 | Steve      | Smith     | steve.smith@example.com | 2003-05-15 | enrolled
(1 row)


university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Bob', 'Johnson', 'bob.johnson@example.com', '2002-08-21', 'enrolled');
INSERT 0 1
university_db=> INSERT INTO enrollments (student_id, course_id, grade) VALUES (2, 1, 'B');
INSERT 0 1
university_db=> select * from enrollments;
 enrollment_id | student_id | course_id | enrollment_date | grade
---------------+------------+-----------+-----------------+-------
             1 |          1 |         1 | 2025-05-30      | A
             2 |          1 |         2 | 2025-05-30      |
             4 |          2 |         1 | 2025-05-30      | B
(3 rows)


university_db=> SELECT * FROM students WHERE student_id = 1;SELECT * FROM enrollments WHERE student_id = 1;DELETE FROM students WHERE student_id = 1; -- Alice
 student_id | first_name | last_name |          email          |    dob     | enrollment_status
------------+------------+-----------+-------------------------+------------+-------------------
          1 | Steve      | Smith     | steve.smith@example.com | 2003-05-15 | enrolled
(1 row)


 enrollment_id | student_id | course_id | enrollment_date | grade
---------------+------------+-----------+-----------------+-------
             1 |          1 |         1 | 2025-05-30      | A
             2 |          1 |         2 | 2025-05-30      |
(2 rows)


DELETE 1
university_db=> SELECT * FROM students WHERE student_id = 1; -- Should be gone
 student_id | first_name | last_name | email | dob | enrollment_status
------------+------------+-----------+-------+-----+-------------------
(0 rows)


university_db=> SELECT * FROM enrollments WHERE student_id = 1;
 enrollment_id | student_id | course_id | enrollment_date | grade
---------------+------------+-----------+-----------------+-------
(0 rows)


university_db=>
```
