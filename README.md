#Postgre SQL
PostgreSQL is one of the best SQL Database, and it is Open Source. It has been used by numerous organizations, if you know supabase, they use postgresql for the database. 
You can modify anything from database secret to docker volumne name. To do so, create .env file in the same directory as the docker-compose.yml file, and add the required environment varibale with your desired value.

DB_CONTAINER="docker-container-name"

DB_DATABASE="yourdatabasenname"

DB_USERNAME="yourdatabaseuser"

DB_PASSWORD="yourdatabasepassword"

For instance, the line POSTGRES_DB=${DB_DATABASE:-postgres} utilizes DB_DATABASE variable from the environment variable file (.env) to set the POSTGRES_DB, and if the variable does not exist, it defaullt to postgres.

You might have noticed another service named pgweb, it’s a simple and minimal web tools build in go to manage postgresql database that you can deploy on your machine. It is optional, but I personally use this tool while developing anything with PostgreSQL.”

#MySQL
It’s not complete when you talk about database without mentioning MySQL. Which is one of the most popular SQL Databases. The command attributes allows you to add some options to the default MySQL configuration, for example you want to use mysql_native_password as authentication plugin instead of caching_sha2_password (the default authentication plugin for MySQL 8.0 or higher). Additionally, you can change the default encoding to UTF-8 (--character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci), and any other options that MySQL supports. MySQL by default need root password, and you need to specify one of the following as an environment variable:

MYSQL_ROOT_PASSWORD, to add root password
MYSQL_ALLOW_EMPTY_PASSWORD, to use empty password for root user (not recommended)
MYSQL_RANDOM_ROOT_PASSWORD, set to yes or true to use random generated password. The generated root password will be printed to stdout.
For the .env file, you can use this example

DB_CONTAINER="docker-container-name"

DB_ROOT_PASSWORD="your root db password"

DB_DATABASE="yourdatabasenname"

DB_USERNAME="yourdatabaseuser"

DB_PASSWORD="yourdatabasepassword"

#SQL Server
SQL Server is SQL Database developer by Microsoft. SQL Server in Docker was introduced in versions 2017, 2019, and 2022 using Ubuntu-based images. Before 2017, you must install it manually in windows

The different SQL Server compared to MySQL and PostgreSQL, SQL Server needs you to accept their EULA , and use sa or sysadmin user instead of root. To use that docker-compose file, create .env file like this

DB_CONTAINER="sql-server"

DB_PASSWORD="db_password"

#MongoDB
MongoDB is different from the previous three databases. MongoDB is NoSQL (Not Only SQL) database that have collections and text documents containing name-value pairs, respectively.  Like the other databases, create .env file and add the following variables

DB_CONTAINER="container-name"

DB_USERNAME="yourdatabaseuser"

DB_PASSWORD="yourdatabasepassword"
To connect to mongodb database that we created, you can use apps like MongoDB Compass, and use connection string like this mongodb://<username>:<password>@localhost:27017/
