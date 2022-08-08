# Collecting data with streams
```java
import static java.util.stream.Collectors.*;
```
## Reducing and summarizing
---
### Create list of Students
```java
class Student{  
    private String name;  
    private int marks;  
  
    public Student(String name, int marks) {  
        this.name = name;  
        this.marks = marks;  
    }  
  
    public String getName() {  
        return name;  
    }  
  
    public void setName(String name) {  
        this.name = name;  
    }  
  
    public int getMarks() {  
        return marks;  
    }  
  
    public void setMarks(int marks) {  
        this.marks = marks;  
    }  
  
    @Override  
    public String toString() {  
        return "Student{" +  
                "name='" + name + '\'' +  
                ", marks=" + marks +  
                '}';  
    }  
}
```

### Generate Random Student list
```java
Random random = new Random();  
List<Student> students = new ArrayList<>();  
IntStream.rangeClosed(1,10).forEach(i -> {  
    Student student = new Student(i+"",random.nextInt(100));  
    students.add(student);  
});
```
### Find maximum (maxBy)
1. comparingInt
2. comparingLong
3. comparingDouble

*Find the highest marks obtained in the class*

```java
Comparator<Student> studentMarksComparator = Comparator.comparingInt(Student::getMarks);  
Optional<Student> student = students.stream().collect(maxBy(studentMarksComparator));
```

### Minimum (minBy)
*Find the lowest marks obtained in the class*

```java
Comparator<Student> studentMarksComparator = Comparator.comparingInt(Student::getMarks);  
Optional<Student> student = students.stream().collect(minBy(studentMarksComparator));
```

### Sum
*Find total marks obtained in the class*
1. summingInt
2. summingLong
3. summingDouble

```java
int total = students.stream().collect(summingInt(Student::getMarks));
```

### Average
*Find average marks obtained by students*
1. averagingInt
2. averagingLong
3. averagingDouble

```java
Double average = students.stream().collect(averagingInt(Student::getMarks));
```

### Summary Report (Count, Sum, Max, Min and Average)
*Find a report of count, sum, maximum, minimum and average of marks in the class.*
1. summarizingInt
2. summarizingLong
3. summarizingDouble

```java
IntSummaryStatistics intSummaryStatistics = students.stream().collect(summarizingInt(Student::getMarks));  
long count = intSummaryStatistics.getCount();  
int max = intSummaryStatistics.getMax();  
int min = intSummaryStatistics.getMin();  
long sum = intSummaryStatistics.getSum();  
double avg = intSummaryStatistics.getAverage();
```

### Joining Strings
*Print the list of Student names separated by a delimiter*

```java
String names = students.stream().map(Student::getName).collect(joining(","));
```


---
## Generalized summarization with reduction
*Find total marks obtained in the class*

- arg1 - starting value of the reduction operation
- arg2 - function to get mapped marks of a student
- arg3 - BinaryOperator that aggregates two item into a single value

```java
long total = students.stream()
					.collect(reducing(0,Student::getMarks,(i,j) -> i + j));
```



*Find highest marks obtained in the class*
- arg - comparator to compare marks

```java
Optional<Student> studentScoredHighestMarks = students.stream().collect(reducing((d1,d2) -> d1.getMarks() > d2.getMarks() ? d1: d2));
```