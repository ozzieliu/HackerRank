## 1. Asian Population

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```sql
SELECT SUM(CITY.POPULATION)
FROM CITY JOIN COUNTRY
ON CITY.COUNTRYCODE=COUNTRY.CODE
WHERE CONTINENT='Asia';
```

## 2. African Cities

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.

```sql
SELECT CITY.NAME
FROM CITY JOIN COUNTRY
ON CITY.COUNTRYCODE=COUNTRY.CODE
WHERE CONTINENT='Africa';
```

## 3. Average Population of Each Continent

Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

```sql
SELECT COUNTRY.CONTINENT, FLOOR(AVG(CITY.POPULATION))
FROM CITY JOIN COUNTRY
  ON CITY.COUNTRYCODE=COUNTRY.CODE
GROUP BY COUNTRY.CONTINENT;
```
