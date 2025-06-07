

## Some of The Most Important SQL Commands

- `SELECT` - extracts data from a database
- `UPDATE` - updates data in a database
- `DELETE` - deletes data from a database
- `INSERT INTO` - inserts new data into a database
- `CREATE DATABASE` - creates a new database
- `ALTER DATABASE` - modifies a database
- `CREATE TABLE` - creates a new table
- `ALTER TABLE` - modifies a table
- `DROP TABLE` - deletes a table
- `CREATE INDEX` - creates an index (search key)
- `DROP INDEX` - deletes an index

TRUNCATE


```sql
PL Block

CREATE PROCEDURE get_name() 

BEGIN

End;


CALL get_name();
```

can have `in, out, in-out`

```sql
create function get_name(in)
RETURNS varchar(20)
Begin

return "Hello"
END;

SELECT get_name();
```
Can have only one input.

```sql
CREATE PROCEDURE getStudentsByMajor( IN majorName varchar(100))
BEGIN
	SELECT StudentID, name, Email
	FROM Student
	Where Major = majorName
End;


CALL GetStudentByMajor('Computer Science');
```

Insert New Enrollment
```sql
Create proedure EnrollStudent(
	IN stuID INT,
	IN courseID INT,
	IN semester varchar(50)
)
BEGIN
	INSERT INTO Enrollement(StudentID, CourseID, Semseter)
	VALUES (stuID, courseID, semester)
END;

CALL EnrollStudent('', '', '');
```

