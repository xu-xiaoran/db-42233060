# 本周作业（第2次作业）
## 题目一（3分）
假设拟在数据库添加一个关系，其关系模式是 users(name, pswd, gender)，并让`name`作为主码。请使用`CREATE TABLE`命令添加该关系。
```sql
CREATE TABLE users(
    name VARCHAR(30),
    pswd VARCHAR(30) NOT NULL,
    gender CHAR(1),
    primary key(name)
);
```

## 题目二（2分+3分）
考虑课堂中使用的`大学`数据库，包括如下关系：
- course(course_id, title, dept_name, credits)
- instructor(ID, name, dept_name, salary)
- teaches(ID, course_id, sec_id, semester, year)
- student(ID, name, dept_name, tot_cred)
- takes(ID, course_id, sec_id, semester, year, grade)

使用SQL语句完成下面的查询：

1. 找到在`计算机`学院开设的不少于`3`个`学分`的课程，并按`学分`进行升序排序。
2. 找到所有被名叫`图灵`的老师教过的学生的学号（`ID`），并确保结果没有重复。
```sql
SELECT course_id, title, dept_name, credits
FROM course
WHERE dept_name = '计算机' AND credits >= 3
ORDER BY credits ASC;
```
```sql
SELECT DISTINCT takes.ID
FROM takes
JOIN teaches ON takes.course_id = teaches.course_id
              AND takes.sec_id = teaches.sec_id
              AND takes.semester = teaches.semester
              AND takes.year = teaches.year
JOIN instructor ON teaches.ID = instructor.ID
WHERE instructor.name = '图灵';
```
## 题目三（2分）
考虑题目二提到的关系模式，请问下面的SQL语句的含义是什么？
# 查找工资高于会计学院所有教师的教师姓名，并确保没有重复值。
```sql
SELECT DISTINCT T.name
FROM instructor AS T, instructor AS S
WHERE T.salary > S.salary AND S.dept_name = '会计';
```
