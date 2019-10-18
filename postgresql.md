## Postgres initial configurations
To sign in on psql command with postgres user is necessary change this file ``` pg_hba.conf ``` at follow folder:
 > "/etc/postgresql/9.x/main/pg_hba.conf"

In this refered file change those lines:

### FROM
| TYPE | DATABASE | USER | ADDRESS | METHOD | 
| ------ | ------ | ------ | ------ | ------ |
| local | all | all |  | peer |

### TO 
| TYPE | DATABASE | USER | ADDRESS | METHOD |
| ------ | ------ | ------ | ------ | ------ |
| local | all | all |  | md5 |

#### If there are more similar content like above, and not working the command to sign in with postgres, change then.

- *peer* means it will trust the identity (authenticity) of UNIX user. So not asking for a password.

- *md5* means it will always ask for a password, and validate it after hashing with MD5.

- *trust* means it will never ask for a password, and always trust any connection.


## To create a user

- Access psql with postgres: ``` psql -U postgres ``` after put the password, or same enter with psql just, with your actual account.
- Maybe you did want see already registered users, then use this command if already logged: ``` \du ```
- Now, type: 
```sql
CREATE USER youruser WITH ENCRYPTED PASSWORD 'yourpass';
```
- Give him all privileges with: 
```sql
GRANT ALL PRIVILEGES ON DATABASE yourdbname TO youruser;
```

## To create a database

- First you can see all created databases with: ``` \l ```
- Then type: ``` CREATE DATABASE db_name ```;
- Connect with this DB using the command: ``` \c db_name ```
- Now you can make changes, like ``` CREATE TABLE... ```

## Creating and managment a table
- Example:

```sql
CREATE TABLE customer (
  email VARCHAR(50), 
  name VARCHAR(50),
  cpf CHAR(11),
  address VARCHAR(100),
  gender CHAR(1),
  phone VARCHAR(9)
);
```
> OBS: VARCHAR(number) can variate the bits quantity, while just CHAR(number) is fixed to inputed number.

- Now you can see which tables have been created. Type: ``` \dt ```
- Choice a specific table to look with: ``` \d customer ``` 
- Add a new column: 
```sql
ALTER TABLE customer ADD COLUMN ddd INT;
```
*Inserting values to table without put name columns.*
```sql
INSERT INTO customer VALUES(
  'fake@user.com.br', 'Fake User', '00000000000', 'Endereço qualquer', 'M', '000000000', 85
);
```
*Inserting with name columns in order and excluding some columns.*
```sql
INSERT INTO customer(name, gender, email) VALUES ('Test', 'F', 'test@user.com');  
```

## How use select command

```sql
/* Is bad practice use * to get all fields, because use more bits */
SELECT * FROM customer
```

```sql
/* Good practice, choose just the necessary fiekds. */
SELECT name, email, address FROM customer 
```

## DUMP

#### TABLE DUMP ( CREATE A SAMPLE DATA )

```sql
  pg_dump -U postgres -t public.column -t public.column -t public.column -a table_name --inserts > sample_data.sql 
```
#### RESTORE DB WITH DUMP

```sql
psql -U db_user db_name < dump_name.bak
```
