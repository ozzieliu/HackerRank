## Revising the Select Query - 1

Query all columns for all American cities in CITY with populations larger than 100,000. The CountryCode for America is USA.

City Table:

Field | Type
-----|------
ID | Number
NAME | VARCHAR2(17)
COUNTRYCODE | VARCHAR2(3)
DISTRICT | VARCHAR2(20)
POPULATION | NUMBER

```sql
SELECT *
FROM CITY
WHERE POPULATION > 100000 AND COUNTRYCODE='USA';
```

## Revising the Select Query - 2

Query the names of all American cities in CITY with populations larger than 120,000. The CountryCode for America is USA.

```sql
SELECT NAME
FROM CITY
WHERE POPULATION > 120000 AND COUNTRYCODE='USA';
```

## Select All

Query all columns for every row in the CITY table.

```sql
SELECT *
FROM CITY;
```

## Select by ID

Query all columns for a city in CITY with the ID 16611661

```sql
SELECT *
FROM CITY
WHERE ID=1661;
```

## Japanese Cities' Detail

Query the details for all the Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

```sql
SELECT *
FROM CITY
WHERE COUNTRYCODE='JPN'
```

## Japanese Cities' Name

Query the the names of all the Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

```sql
SELECT NAME
FROM CITY
WHERE COUNTRYCODE='JPN';
```

## Weather Observation Station 1

Query a list of CITY and STATE from STATION.

STATION table:

Field | Type
------|------
ID | NUMBER
CITY | VARCHAR2(21)
STATE | VARCHAR2(2)
LAT_N | NUMBER
LONG_W | NUMBER

```sql
SELECT CITY, STATE
FROM STATION;
```

## Weather Observation Station 3

Query a list of CITY names from STATION with even ID numbers only. You may print the results in any order, but must exclude duplicates from your answer.

```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE ID%2=0;
```

## Weather Observation Station 4

Let NUM be the number of CITY entries in STATION, and NUMunique be the number of unique cities. Query the value of NUM−NUMunique from STATION.

In other words, query the number of non-unique CITY names in STATION by subtracting the number of unique CITY entries in the table from the total number of CITY entries in the table.

```sql
SELECT (SELECT COUNT(CITY) FROM STATION) -
(SELECT COUNT(DISTINCT(CITY)) FROM STATION);
```

## Weather Observation Station 5

Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

```sql
SELECT CITY, LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY) DESC
LIMIT 1;

SELECT CITY, LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY)
LIMIT 1;
```

## Weather Observation Station 6

Query the list of CITY names starting with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE SUBSTRING(CITY, 1, 1) IN ('A', 'E', 'I', 'O', 'U');
```

## Weather Observation Station 7

Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE RIGHT(CITY, 1) IN ('A', 'E', 'I', 'O', 'U');
```

## Weather Observation Station 8

Query the list of CITY names from STATION which have vowels as both their first and last characters. Your result cannot contain duplicates.

```sql
SSELECT DISTINCT(CITY)
FROM STATION
WHERE RIGHT(CITY, 1) IN ('A', 'E', 'I', 'O', 'U')
  AND SUBSTRING(CITY, 1, 1) IN ('A', 'E', 'I', 'O', 'U');
```

## Weather Observation Station 9

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE SUBSTRING(CITY, 1, 1) NOT IN ('A', 'E', 'I', 'O', 'U');
```

## Weather Observation Station 10

Query the list of CITY names that does not end with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE RIGHT(CITY, 1) NOT IN ('A', 'E', 'I', 'O', 'U');
```

## Weather Observation Station 11

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE RIGHT(CITY, 1) NOT IN ('A', 'E', 'I', 'O', 'U')
  OR SUBSTRING(CITY, 1, 1) NOT IN ('A', 'E', 'I', 'O', 'U');
```

## Weather Observation Station 12

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT(CITY)
FROM STATION
WHERE RIGHT(CITY, 1) NOT IN ('A', 'E', 'I', 'O', 'U')
  AND SUBSTRING(CITY, 1, 1) NOT IN ('A', 'E', 'I', 'O', 'U');
```

## Higher Than 75 Marks

Query the Name of any student in STUDENTS who scored higher than 7575 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

```sql
SELECT Name
FROM STUDENTS
WHERE Marks>75
ORDER BY RIGHT(Name, 3), ID;
```
