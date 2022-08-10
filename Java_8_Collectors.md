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
long total = students.stream().collect(reducing(0,Student::getMarks,(i,j) -> i + j));
```

- *Can use Aggregating function of Integer class*

```java
int total = students.stream().collect(reducing(0,Student::getMarks,Integer::sum));
```

- *Can use IntStream to get the same result*
```java
int total = students.stream().map(Student::getMarks).reduce(Integer::sum).get();  
// or  
int total = students.stream().mapToInt(Student::getMarks).sum();
```
*Find highest marks obtained in the class*
- arg - comparator to compare marks

```java
Optional<Student> studentScoredHighestMarks = students.stream().collect(reducing((d1,d2) -> d1.getMarks() > d2.getMarks() ? d1: d2));
```

## Grouping
### Student list to learn grouping
```java
List<Student> students = new ArrayList<>();  
students.add(new Student("x", 58));  
students.add(new Student("Y", 68));  
students.add(new Student("A", 68));  
students.add(new Student("B", 77));  
students.add(new Student("C", 58));  
students.add(new Student("E", 26));  
students.add(new Student("F", 77));  
students.add(new Student("G", 96));  
students.add(new Student("I", 93));
```

### Single Level Grouping
*Group students by their obtained marks*

```java
Map<Integer, List<Student>> map = students.stream().collect(groupingBy(Student::getMarks));
```

#### Create a enum Performance class
```java
enum Performance {  
    VERY_POOR, POOR, GOOD, EXCELLENT;  
}
```

*Group students by their performance*

```java
Map<Performance, List<Student>> map = students.stream()  
        .collect(groupingBy(student -> {  
            int marks = student.getMarks();  
            if (marks <= 30) {  
                return Performance.VERY_POOR;  
            } else if (marks < 50 && marks > 30) {  
                return Performance.POOR;  
            } else if (marks < 70 && marks > 50) {  
                return Performance.GOOD;  
            } else {  
                return Performance.EXCELLENT;  
            }  
        }));
// Print the map
map.keySet().stream()  
        .forEach(performance -> {  
            System.out.println(performance + "-" + map.get(performance));  
        });
```

>output

>EXCELLENT-[Student{name='B', marks=77}, Student{name='F', marks=77}, Student{name='G', marks=96}, Student{name='I', marks=93}]
	GOOD-[Student{name='x', marks=58}, Student{name='Y', marks=68}, Student{name='A', marks=68}, Student{name='C', marks=58}]
	VERY_POOR-[Student{name='E', marks=26}]


### Multi-Level Grouping
*Group students based on marks and then on their performance category*

```java
Map<Integer, Map<Performance, List<Student>>> map = students.stream()  
        .collect(groupingBy(Student::getMarks, groupingBy(student -> {  
            int marks = student.getMarks();  
            if (marks <= 30) {  
                return Performance.VERY_POOR;  
            } else if (marks < 50 && marks > 30) {  
                return Performance.POOR;  
            } else if (marks < 70 && marks > 50) {  
                return Performance.GOOD;  
            } else {  
                return Performance.EXCELLENT;  
            }  
        })));  
map.keySet().stream()  
        .forEach(performance -> {  
            System.out.println(performance + "-" + map.get(performance));  
        });
```

>Output

>96-{EXCELLENT=[Student{name='G', marks=96}]}
68-{GOOD=[Student{name='Y', marks=68}, Student{name='A', marks=68}]}
26-{VERY_POOR=[Student{name='E', marks=26}]}
58-{GOOD=[Student{name='x', marks=58}, Student{name='C', marks=58}]}
93-{EXCELLENT=[Student{name='I', marks=93}]}
77-{EXCELLENT=[Student{name='B', marks=77}, Student{name='F', marks=77}]}

### Collecting Data in Subgroups
*Count the number of students in each performance category*

```java
Map<Performance, Long> map = students.stream()  
        .collect(groupingBy(student -> {  
            int marks = student.getMarks();  
            if (marks <= 30) {  
                return Performance.VERY_POOR;  
            } else if (marks < 50 && marks > 30) {  
                return Performance.POOR;  
            } else if (marks < 70 && marks > 50) {  
                return Performance.GOOD;  
            } else {  
                return Performance.EXCELLENT;  
            }  
        }, counting()));  
map.keySet().stream()  
        .forEach(performance -> {  
            System.out.println(performance + "-" + map.get(performance));  
        });
```

>Output

>EXCELLENT-4
GOOD-4
VERY_POOR-1

*Get the Student scored highest marks in each performace category*

```java
Map<Performance, Optional<Student>> map = students.stream()  
        .collect(groupingBy(student -> {  
            int marks = student.getMarks();  
            if (marks <= 30) {  
                return Performance.VERY_POOR;  
            } else if (marks < 50 && marks > 30) {  
                return Performance.POOR;  
            } else if (marks < 70 && marks > 50) {  
                return Performance.GOOD;  
            } else {  
                return Performance.EXCELLENT;  
            }  
        }, maxBy(Comparator.comparingInt(Student::getMarks))));  
map.keySet().stream()  
        .forEach(performance -> {  
            System.out.println(performance + "-" + map.get(performance));  
        });
```

>Output

>EXCELLENT-Optional[Student{name='G', marks=96}]
GOOD-Optional[Student{name='Y', marks=68}]
VERY_POOR-Optional[Student{name='E', marks=26}]

*Get rid of Optional in this case (collectingAndThen)*

```java
Map<Performance, Student> map = students.stream()  
        .collect(groupingBy(student -> {  
            int marks = student.getMarks();  
            if (marks <= 30) {  
                return Performance.VERY_POOR;  
            } else if (marks < 50 && marks > 30) {  
                return Performance.POOR;  
            } else if (marks < 70 && marks > 50) {  
                return Performance.GOOD;  
            } else {  
                return Performance.EXCELLENT;  
            }  
        }, collectingAndThen(maxBy(Comparator.comparingInt(Student::getMarks)), Optional::get)));  
map.keySet().stream()  
        .forEach(performance -> {  
            System.out.println(performance + "-" + map.get(performance));  
        });
```

>Output

>EXCELLENT-Student{name='G', marks=96}
GOOD-Student{name='Y', marks=68}
VERY_POOR-Student{name='E', marks=26}

*Sum of marks obtained by students in each performace category*

```java
Map<Performance, Integer> map = students.stream()  
        .collect(groupingBy(student -> {  
            int marks = student.getMarks();  
            if (marks <= 30) {  
                return Performance.VERY_POOR;  
            } else if (marks < 50 && marks > 30) {  
                return Performance.POOR;  
            } else if (marks < 70 && marks > 50) {  
                return Performance.GOOD;  
            } else {  
                return Performance.EXCELLENT;  
            }  
        }, summingInt(Student::getMarks)));  
map.keySet().stream()  
        .forEach(performance -> {  
            System.out.println(performance + "-" + map.get(performance));  
        });
```

>Output

>EXCELLENT-343
GOOD-252
VERY_POOR-26

