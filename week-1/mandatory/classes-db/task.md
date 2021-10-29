# Class Database

## Submission

Below you will find a set of tasks for you to complete to set up a databases of students and mentors.

To submit this homework write the correct commands for each question here:

```sql
-- Create a new table `mentors`, for each mentor we want to save their name, how many years they lived in Glasgow, 
-- their address and their favourite programming language.

create table mentors (
	id serial primary key,
	name varchar(30) not null,
	years_in_glasgow int not null,
	address varchar(120),
	favourite_programming_language varchar(30)
);

-- Create a new table `students`, for each student we want to save their name, address and if they have 
-- graduated from Code Your Future.

create table students (
	id serial primary key,
	name varchar(30) not null,
	address varchar(120),
	graduated boolean not null,
);

-- Create a new `classes` table to record the following information:

   -- A class has a leading mentor
   -- A class has a topic (such as Javascript, NodeJS)
   -- A class is taught at a specific date and at a specific location

create table classes (
	id serial primary key,
	mentor_id int references mentors(id),
	-- We now want to store who among the students attends a specific class. How would you store that?
	-- Come up with a solution and insert some data if you model this as a new table.
	student_id int references students(id),
	topic varchar(60) not null,
	date_of_class date not null,
	location_of_class varchar(120) not null
);

-- Insert 5 mentors in the `mentors` table (you can make up the data, it doesn't need to be accurate ;-))

insert into mentors (name, years_in_glasgow, address, favourite_programming_language) 
values ('Jonas Schmitt', 2, '22 king St', 'Phyton');

insert into mentors (name, years_in_glasgow, address, favourite_programming_language) 
values ('Emily Susana', 10, '55 Chisholm St', 'Java');

insert into mentors (name, years_in_glasgow, address, favourite_programming_language) 
values ('Stephanny Zapata', 5, '25 New Wynd', 'Javascript');

insert into mentors (name, years_in_glasgow, address, favourite_programming_language) 
values ('Omar Ascanio', 15, '10 Albion St', 'C#');

insert into mentors (name, years_in_glasgow, address, favourite_programming_language) 
values ('Virginia Chin', 1, '05 Parnie St', 'C++');


-- Insert 10 students in the `students` table.

insert into students (name, address, graduated) values ('Eduardo Arias', '30 Trongate', true);
insert into students (name, address, graduated) values ('Liliana Bautista', '12 Old Wynd', false);
insert into students (name, address, graduated) values ('Camila Ruiz', '15 Buchanan St', true);
insert into students (name, address, graduated) values ('Bianca Inga', '18 Anchor Ln', true);
insert into students (name, address, graduated) values ('Anthony Ure', '58 St Vicent Pl', true);
insert into students (name, address, graduated) values ('Fabian Ortiz', '109 Queen St', false);
insert into students (name, address, graduated) values ('Carlos Velasquez', '70 Miller St', true);
insert into students (name, address, graduated) values ('Jesus Turizo', '32 Virginia St', true);
insert into students (name, address, graduated) values ('Nancy Peña', '45 Arguely', true);
insert into students (name, address, graduated) values ('Wilson Lozano', '60 Stockwell St', false);

-- Verify that the data you created for mentors and students are correctly stored in their respective tables 
-- (hint: use a `select` SQL statement).

-- show me all mentors
select * from mentors;

-- show me all students
select * from students;


-- Insert a few classes in the `classes` table
insert into classes (mentor_id, student_id, topic, date_of_class, location_of_class) values (1, 10, 'Phyton', '2021-10-18', 'Glasgow G12 8QQ');
insert into classes (mentor_id, student_id, topic, date_of_class, location_of_class) values (1, 2, 'Phyton', '2021-10-18', 'Glasgow G12 8QQ');
insert into classes (mentor_id, student_id, topic, date_of_class, location_of_class) values (3, 3, 'Javascript', '2021-10-20', 'Cowcaddens Rd');
insert into classes (mentor_id, student_id, topic, date_of_class, location_of_class) values (3, 7, 'Javascript', '2021-10-20', 'Cowcaddens Rd');
insert into classes (mentor_id, student_id, topic, date_of_class, location_of_class) values (2, 1, 'Java', '2021-10-22', '16 Richmond St');
insert into classes (mentor_id, student_id, topic, date_of_class, location_of_class) values (2, 4, 'Java', '2021-10-22', '16 Richmond St');
insert into classes (mentor_id, student_id, topic, date_of_class, location_of_class) values (4, 6, 'C#', '2021-10-29', 'Technology Ave, Blantyre');
insert into classes (mentor_id, student_id, topic, date_of_class, location_of_class) values (4, 9, 'C#', '2021-10-29', 'Technology Ave, Blantyre');
insert into classes (mentor_id, student_id, topic, date_of_class, location_of_class) values (5, 5, 'C++', '2021-09-15', 'Hetherington Building, Bute Ln');
insert into classes (mentor_id, student_id, topic, date_of_class, location_of_class) values (5,	8, 'C++', '2021-09-15', 'Hetherington Building, Bute Ln');

-- Answer the following questions using a `select` SQL statement:

-- Retrieve all the mentors who lived more than 5 years in Glasgow
select * from mentors where years_in_glasgow > 5;

-- Retrieve all the mentors whose favourite language is Javascript
select * from mentors where favourite_programming_language = 'Javascript';

-- Retrieve all the students who are CYF graduates
select * from students where graduated = true;

-- Retrieve all the classes taught before June this year
select * from classes where date_of_class < '2021-06-01';

-- Retrieve all the students (retrieving student ids only is fine) who attended the Javascript class 
-- (or any other class that you have in the `classes` table).
select student_id from classes where topic='Javascript'; 
```

When you have finished all of the questions - open a pull request with your answers to the `Databases-Homework` repository.

## Task

1. Create a new database called `cyf_classes` (hint: use `createdb` in the terminal)
2. Create a new table `mentors`, for each mentor we want to save their name, how many years they lived in Glasgow, their address and their favourite programming language.
3. Insert 5 mentors in the `mentors` table (you can make up the data, it doesn't need to be accurate ;-)).
4. Create a new table `students`, for each student we want to save their name, address and if they have graduated from Code Your Future.
5. Insert 10 students in the `students` table.
6. Verify that the data you created for mentors and students are correctly stored in their respective tables (hint: use a `select` SQL statement).
7. Create a new `classes` table to record the following information:

   - A class has a leading mentor
   - A class has a topic (such as Javascript, NodeJS)
   - A class is taught at a specific date and at a specific location

8. Insert a few classes in the `classes` table
9. We now want to store who among the students attends a specific class. How would you store that? Come up with a solution and insert some data if you model this as a new table.
10. Answer the following questions using a `select` SQL statement:
    - Retrieve all the mentors who lived more than 5 years in Glasgow
    - Retrieve all the mentors whose favourite language is Javascript
    - Retrieve all the students who are CYF graduates
    - Retrieve all the classes taught before June this year
    - Retrieve all the students (retrieving student ids only is fine) who attended the Javascript class (or any other class that you have in the `classes` table).
