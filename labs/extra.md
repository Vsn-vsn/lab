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

```cpp
class Solution {
  public:
    void mergeSort(vector<int>& arr, int l, int r) {
        if(l >= r) return;
        int mid = (l+r)/2;
        mergeSort(arr, l,mid);
        mergeSort(arr,mid+1, r);
        merge(arr,l,mid,r);
    }
    void merge(vector<int>& arr, int low, int mid, int high){
        vector<int> temp;
        int left = low;
        int right = mid + 1;
        while(left <= mid && right <= high){
            if(arr[left] <= arr[right])
                temp.push_back(arr[left++]);
            else temp.push_back(arr[right++]);
        }
        while(left <= mid)
            temp.push_back(arr[left++]);
        while(right <= high)
            temp.push_back(arr[right++]);
        for(int i = low; i <= high; i++)
            arr[i] = temp[i - low];
    }
};
```

```cpp
class Solution {
  public:
    void quickSort(vector<int>& arr, int low, int high) {
        if(low >= high) return;
        int part = partition(arr, low, high);
        quickSort(arr, low, part - 1);
        quickSort(arr, part + 1, high);
    }

  public:
    int partition(vector<int>& arr, int low, int high) {
        int p = low;
        int i = low;
        int j = high;
        while (i < j){
            while(arr[i] <= arr[p] && i < high) i++;
            while(arr[j] > arr[p] && j >= low + 1) j--;
            if(i < j){ 
                swap(arr[i], arr[j]);
            }
        }
        swap(arr[j], arr[p]);
        return j;
    }
};
```


