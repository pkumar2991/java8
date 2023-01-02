# Java 8 Date & Time Enhancement
### Problems with existing **java.util.Date** & **java.util.calendar** api:
- Not thread safe
- APIs are poorly designed
- Explicit handling of time zone

### Enhancement 
- Date & Time APIs are thread safe
- APIs are well designed and they are easy to use and understand
- No explict handling of time zone
- Introduced as new package - **java.time**

### LocalDate
Returns the local date without  time zone

```java
LocalDate date = LocalDate.now();
```

Output: `2022-12-24`

Parse the date into Localdate

```java
LocalDate parsedDate = LocalDate.of(2023,11,25);
```

Output: `2023-11-25`

Parsed the date from String

```java
LocalDate parsedDate = LocalDate.parse("2023-12-26");
```

Output: `2023-12-26`

#### Utilities method to play with date

Add one day to the current date

```java
LocalDate date = LocalDate.now().plusDays(1);
```

Output: `2022-12-25`

Add one month to the current date

```java
LocalDate date = LocalDate.now().plusMonths(1);
```

Output: `2023-01-24`

Subtract one month from the current date

```java
LocalDate date = LocalDate.now().minus(1, ChronoUnit.MONTHS);
```

Output: `2022-11-24`

Verify if the year of the date is Leap year

```java
Boolean isLeapYear = LocalDate.now().isLeapYear();
```

Validate if the date is **before or after** the given date

```java
boolean isBefore = LocalDate.now().isBefore(LocalDate.of(2023,12,25));
```

Output: `true`

### LocalTime
Returns time without date

Get the current time of the system clock

```java
LocalTime timeNow = LocalTime.now();
```

Output: `17:07:21.104463900`

Parse the time in String into LocalTime

```java
LocalTime timeNow = LocalTime.parse("05:30");
```

Output: `05:30`

Get LocalTime object using Of method

```java
LocalTime timeNow = LocalTime.of(5,30);
System.out.println(timeNow instanceof LocalTime);
System.out.println(timeNow);
```

Output:
`true`
`05:30`

#### Utilities method to play with time
Various utility methods to add, minus, get minutes or hours of/to the time

```java
LocalTime timeNow = LocalTime.of(5,30).plus(1, ChronoUnit.HOURS);
LocalTime timeNow = LocalTime.of(5,30).plus(1, ChronoUnit.MINUTES);
LocalTime timeNow = LocalTime.of(5,30).minusHours(1);
LocalTime timeNow = LocalTime.of(5,30).minusMinutes(1);
long hour = LocalTime.of(5,30).getHour();
long min = LocalTime.of(5,30).getMinute();
```

Validate if the one time is before/after of another time

```java
boolean isBefore = LocalTime.now().isBefore(LocalTime.of(18,30));
```

Print time with AM/PM and in 12 hour format

```java
LocalTime.parse("05:30").format(DateTimeFormatter.ofPattern("hh:mm a"));  
```

Output: `05:30 AM`

Get min, max , noon and midnight time

```java
LocalTime time = LocalTime.MAX;
```

Output: `23:59:59.999999999`

```java
LocalTime time = LocalTime.MIN;
```

Output: `00:00`

```java
LocalTime time = LocalTime.NOON;
```

Output: `12:00`

```java
LocalTime time = LocalTime.MIDNIGHT;
```

Output: `00:00`

### LocalDateTime
Returns an object having date and time information all together

