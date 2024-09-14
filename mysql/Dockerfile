# official image it run automatically.
FROM mysql:8.0 
# not a human, only for system
RUN adduser -r expense
# set up the root user----pwd,user----id,pwd,db
ENV MYSQL_ROOT_PASSWORD=ExpenseApp@1 \
    MYSQL_USER=expense \
    MYSQL_PASSWORD=ExpenseApp@1 \
    MYSQL_DATABASE=transactions
    # change the owner ship to /var/lib/mysql to /var/run/mysqld
RUN chown -R expense:expense /var/lib/mysql /var/run/mysqld
# .sql files moved into server initialization or entrypoint.when server init that time only schema also loaded.
COPY scripts/*.sql /docker-entrypoint-initdb.d/