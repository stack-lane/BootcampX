# Assignment 006 (Carbon)

> This assignment is due by 12:30 PM, 20 March 2025.
>
> Once you've completed the assignment, submit it over [here](https://forms.gle/1KHZW8o8r5tBvCbz8).

_**NOTE: Your assignment repository should be named `carbon`.**_

## Database Structure

Create a `College` database that --

has the following entities on it

1. `Student` <br/> Contains details about each individual student and has the following columns on it:

   - `id` (`primary key, uuid`)
   - `name`
   - `dateOfBirth`
   - `aadharNumber` (`unique`)

2. `Professor` <br/> Contains details about each individual professor and has the following columnts on it:

   - `id`
   - `name`
   - `seniority` (`JUNIOR`, `SENIOR`, `ASSOCIATE`, `HEAD`)
   - `aadharNumber` (`unique`)

and has following relationships

3. `Proctorship` <br/> A relationship specifying a list of students who come under a given professor's protorship. Every student will have exactly one proctor (professor). Each professor can have many students under his proctorship.

4. `LibraryMembership` <br/> Contains library membership details for each student and has the following columns on it:

   - `id` (`primary key, uuid`)
   - `studentId` (`foreign key, unique`) <br/> References the `id` of the `Student` entity.
   - `issueDate`
   - `expiryDate`

   Each student can have exactly one library membership, and each library membership belongs to exactly one student.

# REST API Structure

Create a REST API for this `College` database with the following end-points

1. `GET` `/students` <br/> Returns all the students in the college.
2. `Get` `/students/enriched` <br/> Returns all the studnets in the college along with the proctor details for each of the students returned.
3. `GET` `/professors` <br/> Returns all the professors in the college.
4. `POST` `/students` <br/> Creates a new student (ensure no duplicates on the basis of `aadharNumber`).
5. `POST` `/professors` <br/> Creates a new professor (ensure no duplicates on the basis of `aadharNumber`).
6. `GET` `/professors/:professorId/proctorships` <br/> Returns all students under the proctorship of the given professor.
7. `PATCH` `/students/:studentId` <br/> Updates the details of a student by their `id`.
8. `PATCH` `/professors/:professorId` <br/> Updates the details of a professor by their `id`.
9. `DELETE` `/students/:studentId` <br/> Deletes a student by their `id`.
10. `DELETE` `/professors/:professorId` <br/> Deletes a professor by their `id`.
11. `POST` `/professors/:professorId/proctorships` <br/> Assigns a student under the protorship of the professor referenced by `professorId`.
12. `GET` `/students/:studentId/library-membership` <br/> Returns the library membership details of the specified student.
13. `POST` `/students/:studentId/library-membership` <br/> Creates a library membership for the specified student. Ensure no duplicate library memberships for a student.
14. `PATCH` `/students/:studentId/library-membership` <br/> Updates the library membership details of the specified student.
15. `DELETE` `/students/:studentId/library-membership` <br/> Deletes the library membership of the specified student.
