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


### Store people, houses and addresses
POST

| VERB        | PATH.     | ACTION    |
| POST        | /houses   |  create   |
| POST        | /people   | create    |
| POST        | /address  | create    |


### Look up a house, its address and owner
GET




### Look up people in our neighbourhood within certain age brackets and with specific household sizes
GET






