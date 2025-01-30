```sql
--1--
SELECT course_id, COUNT(DISTINCT id) AS num_students
FROM takes
GROUP BY course_id;

--2--
SELECT course.dept_name, AVG(stu_count) AS avg_students
FROM course1 
JOIN (
    SELECT course_id, COUNT(DISTINCT id) AS stu_count
    FROM takes1
    GROUP BY course_id
) course_stu
ON course_stu.course_id = course1.course_id
GROUP BY course1.dept_name
HAVING AVG(stu_count) > 10;

--3--
SELECT dept_name, COUNT(course_id) AS total
FROM course1
GROUP BY dept_name;

--4--
SELECT dept_name, AVG(salary) AS avg
FROM instructor1
GROUP BY dept_name
HAVING AVG(salary) > 42000;

--5--
SELECT section1.course_id, section1.section_id, COUNT(DISTINCT takes1.id) AS stud
FROM section1
LEFT JOIN takes1 ON section1.course_id = takes1.course_id
  AND section1.semester = takes1.semester
  AND section1.year = takes1.year
WHERE section1.semester = 'Spring' AND section1.year = 2009
GROUP BY section1.course_id, section1.section_id;

--6--
SELECT course1.course_id, prereq1.prereq_id
FROM course1
JOIN prereq1 ON course1.course_id = prereq1.course_id
ORDER BY course1.course_id;

--7--
SELECT id, name, dept_name, salary
FROM instructor1
ORDER BY salary DESC;

--8--
SELECT dept_name, AVG(salary) AS avg
FROM instructor1
GROUP BY dept_name
HAVING AVG(salary) > 42000;

--9--


--10--



--11--


--12--

  );

--14--


--15--


--16--


--17--


--18--


```
[lnk](https://github.com/AniGP/MIT-Manipal-CSE-Labs-2022/blob/c71b69a87346b45bff12354e46a95ef000886525/Semester-4/DBS/Week5/Week5_Commands_LabSoln.sql)