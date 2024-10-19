FROM mysql:8.0
ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 
ADD scripts/*.sql /docker-entrypoint-initdb.d
    # MYSQL_DATABASE=transactions \
    # MYSQL_USER=expense \
    # MYSQL_PASSWORD=ExpenseApp@1

# Initializing a fresh instance
# When a container is started for the first time, a new database with the specified name will be created and initialized with the provided configuration variables. Furthermore, it will execute files with extensions .sh, .sql and .sql.gz that are found in /docker-entrypoint-initdb.d.