MySQL to PostgreSQL Converter
=============================

Lanyrd's MySQL to PostgreSQL conversion script. Use with care.

This script was designed for our specific database and column requirements -
notably, it doubles the lengths of VARCHARs due to a unicode size problem we
had, places indexes on all foreign keys, and presumes you're using Django
for column typing purposes.

How to use
----------

First, dump your MySQL database in PostgreSQL-compatible format

    mysqldump --compatible=postgresql --default-character-set=utf8 \
    -r databasename.mysql -u root databasename

Then, convert it using the dbconverter.py script

`python db_converter.py databasename.mysql databasename.psql`

It'll print progress to the terminal.

Finally, load your new dump into a fresh PostgreSQL database using: 

`psql -f databasename.psql`

Changed by Alina Soboleva for Python 3.x
