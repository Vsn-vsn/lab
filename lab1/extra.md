```sql
--5--
SELECT c.course_id, c.title
FROM course c
WHERE c.course_id IN (
    SELECT course_id 
    FROM section 
    WHERE semester = 'Fall' AND year = 2009
    INTERSECT
    SELECT course_id 
    FROM section 
    WHERE semester = 'Spring' AND year = 2010
);

--6--
SELECT COUNT(DISTINCT takes.id) AS total_students
FROM takes
WHERE takes.course_id IN (
    SELECT teaches.course_id
    FROM teaches
    WHERE teaches.id = 10101
);

--7--
SELECT course_id
FROM section
WHERE semester = 'Fall' AND year = 2009
  AND course_id NOT IN (
      SELECT course_id
      FROM section
      WHERE semester = 'Spring' AND year = 2010
  );

--9--
SELECT name
FROM instructor
WHERE salary > SOME (
    SELECT salary
    FROM instructor
    WHERE dept_name = 'Biology'
);

--10--
SELECT name
FROM instructor
WHERE salary > ALL (
    SELECT salary
    FROM instructor
    WHERE dept_name = 'Biology'
);

--11--
SELECT dept_name
FROM instructor
GROUP BY dept_name
HAVING AVG(salary) = (
    SELECT MAX(avg_salary)
    FROM (
        SELECT AVG(salary) AS avg_salary
        FROM instructor
        GROUP BY dept_name
    ) AS dept_avg
);

--12--
SELECT dept_name
FROM department
WHERE budget < (
    SELECT AVG(salary)
    FROM instructor
);

--13--
SELECT DISTINCT course_id
FROM section s1
WHERE semester = 'Fall' AND year = 2009
  AND EXISTS (
      SELECT 1
      FROM section s2
      WHERE s1.course_id = s2.course_id
        AND s2.semester = 'Spring' AND s2.year = 2010
  );

--14--
SELECT id
FROM student s
WHERE NOT EXISTS (
    SELECT course_id
    FROM course
    WHERE dept_name = 'Biology'
      AND course_id NOT IN (
          SELECT course_id
          FROM takes
          WHERE takes.id = s.id
      )
);

--15--
SELECT course_id
FROM section
WHERE year = 2009
GROUP BY course_id
HAVING COUNT(*) <= 1;

--16--
SELECT takes.id
FROM takes
JOIN course ON takes.course_id = course.course_id
WHERE course.dept_name = 'CSE'
GROUP BY takes.id
HAVING COUNT(DISTINCT takes.course_id) >= 2;

--17--
SELECT dept_name, AVG(salary) AS avg_salary
FROM instructor
GROUP BY dept_name
HAVING AVG(salary) > 42000;

--18--


```