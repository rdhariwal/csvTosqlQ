# query your csv files like sql

###Prerequistes
* Sqlite3 
    * for linux: `sudo apt-get install sqlite3 libsqlite3-dev`
    * for mac: `brew install sqlite3`

start sqllite3 shell by running
`````
sqlite3
`````
    
use the `.mode` command as follows to set it to csv:

`````
sqlite> .mode csv
`````
 use the `.import FILE TABLE` command to import the data from the city.csv file into the cities table.
 ````` 
.import city.csv cities
`````
If the table does not previously exist, the first row of the CSV file is interpreted to be column names and the actual data starts on the second row of the CSV file.

To verify the import, you use the `.schema` command to display the structure of the cities table.
`````
.schema cities
`````

Query against the imported table by:
````
SELECT name, population FROM cities;
````
See if you can spot the problem between these two group of queries (hint: is population order by working?):
````
SELECT name, population FROM cities order by population desc;
SELECT name, population FROM cities order by population asc;

SELECT name, population FROM cities order by name asc;
SELECT name, population FROM cities order by name desc;
````

Drop table by:
````
DROP TABLE cities;
````

Create table:
````
CREATE TABLE cities (
  name Varchar,
  population Int
);
````

Import csv file again but now in an existing table with population as Int and no headers
````
.import city_no_headers.csv cities
````

Try these queries again. because the table existed with population as Int the `order by` behaviour is correct: 
````
SELECT name, population FROM cities order by population desc;
SELECT name, population FROM cities order by population asc;

SELECT name, population FROM cities order by name asc;
SELECT name, population FROM cities order by name desc;
````


    
