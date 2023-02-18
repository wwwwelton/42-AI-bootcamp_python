## PISCINE PYTHON DJANGO
### D05 - DATABASES

##### POSTGRESQL SETUP
```bash
# install postgres
# install based in you OS

# enter in a postgres database "postgres"
psql -d postgres

# inside postgres
# help/manual
\?

# list available databases
\l

# list database relations
\d

# create a database called "formationdjango"
# end sql commands with ";"
CREATE DATABASE formationdjango;

# create a database user "djangouser" with password "secret"
CREATE USER djangouser WITH PASSWORD 'secret';

# set "djangouser" to own "formationdjango" database
ALTER DATABASE formationdjango OWNER TO djangouser;

# edit postgres conf to disallow login without password
nano ~/.brew/var/postgres/pg_hba.conf

# in the end of file change network "METHOD" from trust to md5
local   all all trust
local   all 127.0.0.1/32 md5

# restart psql service
sudo systemctl restart postgresql.service
```

##### PSYCOPG2 TABLE CREATION
create_table.py
```python
import psycopg2

if __name__ == '__main__' :
    conn = psycopg2.connect(
            database = 'formationdjango',
            host='localhost',
            user='djangouser',
            password='secret'
            )

    curr = conn.cursor()

    curr.execute(""" CREATE TABLE members (
            id serial PRIMARY KEY,
            firstname varchar(32),
            lastname varchar(32),
            lastname varchar(32),
            birthdate date
            )
            """)

    conn.commit()
    conn.close()
```

drop_table.py
```python
import psycopg2

if __name__ == '__main__' :
    conn = psycopg2.connect(
            database = 'formationdjango',
            host='localhost',
            user='djangouser',
            password='secret'
            )

    curr = conn.cursor()

    curr.execute(""" DROP TABLE Members      """)
    conn.commit()
    conn.close()
```

##### SIMPLE QUERIES
insert_table.py
```python
import psycopg2

if __name__ == '__main__' :
    conn = psycopg2.connect(
            database = 'formationdjango',
            host='localhost',
            user='djangouser',
            password='secret'
            )

    curr = conn.cursor()

    curr.execute("""
            INSERT INTO members(firstname, lastname, birthdate) VALUES
            ('Eric', 'Clapton', '1945-03-30'),
            ('Joe', 'Bonamassa', '1977-05-08')
                    """)

    conn.commit()
    conn.close()
```

select_table.py
```python
import psycopg2

if __name__ == '__main__' :
    conn = psycopg2.connect(
            database = 'formationdjango',
            host='localhost',
            user='djangouser',
            password='secret'
            )

    curr = conn.cursor()

    curr.execute(""" SELECT * FROM members """)
    response = curr.fetchall()
    for row in response :
            print(row)
    conn.close()
```

delete_table.py
```python
import psycopg2

if __name__ == '__main__' :
    conn = psycopg2.connect(
            database = 'formationdjango',
            host='localhost',
            user='djangouser',
            password='secret'
            )

    curr = conn.cursor()

    curr.execute(""" DELETE FROM members
                    WHERE lastname LIKE 'Clapton'
            """)

    conn.commit()
    conn.close()
```

##### SQL MULTIPLES TABLES QUERIES
create_table.py
```python
import psycopg2

if __name__ == '__main__' :
    conn = psycopg2.connect(
            database = 'formationdjango',
            host='localhost',
            user='djangouser',
            password='secret'
            )

    curr = conn.cursor()

    curr.execute(""" CREATE TABLE members (
                    stage_name varchar(64) PRIMARY KEY,
                    firstname varchar(32) NOT NULL,
                    lastname varchar(32) NOT NULL,
                    birthdate date
                    )
    """)

    conn.commit()

    curr.execute(""" CREATE TABLE album (
                    title varchar(128) NOT NULL,
                    artist varchar(32) REFERENCES members(stage_name),
                    live boolean,
                    release date,
                    CONSTRAINT album_pk PRIMARY KEY (title, artist)
                    )
            """)
    conn.commit()

    curr.execute("""
                    INSERT INTO members(stage_name, firstname, lastname, birthdate) VALUES
                    ('Eric Clapton', 'Eric', 'Clapton', '1945-03-30'),
                    ('Joe Bonamassa', 'Joe', 'Bonamassa', '1977-05-08'),
                    ('Slash', 'Saul', 'Hudson', '1965-07-23'),
                    ('Bumblefoot', 'Ronald Jay', 'Bluementhal', '1969-07-25')
                            """)
    conn.commit()

    curr.execute("""
                    INSERT INTO album(title, artist, release, live) VALUES
                    ('Slash', 'Slash', '2010-03-31', false),
                    ('Apocalyptic Love', 'Slash', '2012-05-22', false),
                    ('Normal', 'Bumblefoot', '2005-12-01', false),
                    ('Abnormal', 'Bumblefoot', '2008-08-01', false),
                    ('Live from the Royal Albert Hall', 'Joe Bonamassa', null, true),
                    ('One More Car, One More Rider', 'Eric Clapton', '2002-11-05', true),
                    ('Unplugged', 'Eric Clapton', '1992-08-25', true)
                            """)
    conn.commit()

    conn.close()
```

select_studio_album.py
```python
import psycopg2

if __name__ == '__main__' :
    conn = psycopg2.connect(
            database = 'formationdjango',
            host='localhost',
            user='djangouser',
            password='secret'
            )

    curr = conn.cursor()

    curr.execute("""
                    SELECT a.title, m.firstname, m.lastname, a.release
                    FROM members m JOIN album a
                    ON a.artist = m.stage_name WHERE a.live = false;
                    """)
    response = curr.fetchall()
    conn.close()

    for row in response:
            print("album {:<20} from {:<25} release on {}".format(
                row[0], "{} {}".format(row[1], row[2], row[3].isoformat)))
```

##### DJANGO ORM CONFIGURATION
```bash
```

##### DJANGO MODELS
```bash
```

##### DJANGO MIGRATIONS
```bash
```

##### DJANGO MODEL QUERIES
```bash
```

##### DJANGO MULTIPLE MODEL QUERIES
```bash
```

##### DJANGO FIXTURES
```bash
```
