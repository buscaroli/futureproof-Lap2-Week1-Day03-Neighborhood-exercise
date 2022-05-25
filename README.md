# NEIGHBOURHOOD

## Consider the type of data we will be storing and therefore the type of database we should implement (SQL vs NoSQL)

Because the structure of the data is clearly defined we decided to use a Relational Database like postgreSQL.

## Create a schema for this database

Considering the brief we decided to have three tables:

- Houses

```sql
  id INT
  owner_id INT
  address_id INT
```
- People

```sql
  id INT
  name VARCHAR (20)
  age INT
  household_size INT
```

- Addresses

```sql
  id INT
  postcode VARCHAR(8)
  street_address VARCHAR(40)
```

## Consider the requests our API should be capable of handling

Following the brief we are considering that out database only contains data for one neighbourhood.

### Store people, houses and addresses


| VERB        | PATH.     | ACTION    |
| POST        | /houses   | create    |
| POST        | /people   | create    |
| POST        | /address  | create    |



### Look up a house, its address and owner


| VERB           | PATH.         | ACTION   |
| GET            | /houses/:id   |  show    |
| GET            | /people/:id   |  show    |
| GET            | /address/:id  |  show    |



### Look up people in our neighbourhood within certain age brackets and with specific household sizes



| VERB           | PATH.         | ACTION    |
| GET            | /people       |  index    |

#### Query

##### User enter data into a form
The address bar would look like this:

`Browser Address bar: http://neighbourhood.com/people?minAge=18&maxAge=35&householdGreaterThan=4`

##### Example of a javascript query 
fetch(`http://neighbourhood.com/people?minAge=${minAge}&maxAge=${maxAge}&householdGreaterThan=${hgt}`

##### Example of the object that coul dbe sent

```
{
minAge = 18,
maxAge = 35,
householdGreaterThan = 4
}
```

##### Example of a postgreSQL query

```sql
  SELECT * from people WHERE age GT minAge
```




