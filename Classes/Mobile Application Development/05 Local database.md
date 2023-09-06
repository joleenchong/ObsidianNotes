SQLite is basically same syntax as MySQL.

But we use Android Room:
- annotations define entities (tables) and Data Access Objects (DAOs)
	- code for db operations generated at compile time
	- queries are type-safe

Steps:
- put following into build.gradle file and press sync now
```java
dependencies {
	...
	implementation "androidx.room:room-runtime:2.4.8"
	annotationProcessor "androidx.room:room-compiler:2.4.8"
}
```
- define entities using `@Entity`
	- `@PrimaryKey` specifies primary key of entity
		- can also use primaryKeys property for `@Entity` for composite primary keys
	- `@ColumnInfo` specifies column properties
	- `@Ignore` makes annotated field not have a defined column in entity
	- read more about `@Index`
```Java
import androidx.room.ColumnInfo;
import androidx.room.Entity;
import androidx.room.PrimaryKey;

@Entity(tableName = "students")
public class Student {
	@PrimaryKey(autoGenerate = true)
	private long id;

	@ColumnInfo(name = "student_name")
	private String name;

}

// Composite keys
@Entity(primaryKeys = {"firstName", "lastName"})
public class User {
	public String firstName;
	public String lastName;
	
	@Ignore
	String picture;
}
```
- create DAO to define methods to access database
	- annotations for DAO: `@Insert`, `@Update`, `@Delete`, `@Query`
	- Varargs (`...`) help pass variable number of args of same type to method - treated as array of object instances
```Java
import androidx.room.Dao;

@Dao
public interface StudentDAO
{
	@Insert
	void insert(Student student);
	@Insert
	void insertMultiple(List<Student> students);

	@Update //this works based on primary key defined
	void update(Student studnet);
	@Update
	void updateMultiple(List<Student> students);

	@Delete
	void delete(Student student);
	@Delete
	void deleteMultiple(List<Student> students);

	//varargs example
	void insert(Student... student);

	@Query("SELECT * FROM students")
	List<Student> getAllStudents();
	//query with parameters, can use AND / OR for multiple
	@Query("SELECT * FROM students WHERE name = :studentName")
	List<Student> getStudentsByName(String studentName);
}
```
- create database class
```Java
import androidx.room.Database;
import androidx.room.RoomDatabase;

@Database(entities = {Student.class}, version = 1)
public abstract class StudentDatabase extends RoomDatabase
{
	public abstract StudentDAO studentDAO();
}

```
- init database class using Singleton pattern (allowMainThreadQueries is not recommended)
```Java
public class StudentDBInstance
{
	private static StudentDatabase database;

	public static StudentDatabase getDatabase(Context context)
	{
		if (database == null)
		{
			database = Room.databaseBuilder(context, StudentDatabase.class, "app_database").allowMainThreadQueries().build();
		}
		return database;
	}
}
```
- use Room in activities / fragments - slide 36-37