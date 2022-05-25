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


| VERB        | PATH      | ACTION    |
 ---          | ---       | ---       
| POST        | /houses   | create    |
| POST        | /people   | create    |
| POST        | /address  | create    |

The API will return either:
- an error if the entry already existed
- an notification that the entry has been created


### Look up a house, its address and owner


| VERB           | PATH          | ACTION   |
 ---             | ---           | ---      
| GET            | /houses/:id   |  show    |
| GET            | /people/:id   |  show    |
| GET            | /address/:id  |  show    |

The API will return either:

- an empty array ( [] ) if no match was found
- an array of the appropriate entry (person, house or address) 


### Look up people in our neighbourhood within certain age brackets and with specific household sizes


| VERB           | PATH          | ACTION    |
 ---             | ---           | ---       
| GET            | /people       |  index    |

The API will return either:

- an empty array ( [] ) if no match was found
- an array of the people that match the criteria 


#### Queries

##### User enter data into a form
The address bar would look like this:

`Browser Address bar: http://neighbourhood.com/people?minAge=18&maxAge=35&householdGreaterThan=4`

##### Example of a javascript query 
fetch(`http://neighbourhood.com/people?minAge=${minAge}&maxAge=${maxAge}&householdGreaterThan=${hgt}`

##### Example of the object that could be sent


```js
{
minAge = 18,
maxAge = 35,
householdGreaterThan = 4
}
```

##### Example of a postgreSQL query


```sql
  SELECT *
  FROM people 
  WHERE age BETWEEN minAge AND maxAge 
  AND household_size >= householdGreaterThan;
```


