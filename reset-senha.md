**Resetar Senha Mysql**

1.  Pare o serviço do mysql: ***$ sudo service mysql stop;***
2. Não carregar as permissões: ***$ sudo mysqld_safe --skip-grant-tables &;***
3. Caso ocorra o seguinte erro:
> mysqld_safe Logging to '/var/log/mysql/error.log'.
mysqld_safe Logging to '/var/log/mysql/error.log'.
mysqld_safe Directory '/var/run/mysqld' for UNIX socket file don't exists.

Use o seguinte comando: 
>**$ sudo mkdir -p /var/run/mysqld**
**$ sudo chown mysql:mysql /var/run/mysqld**

Ou

> **$ sudo mkdir -p /var/run/mysql**
**$ sudo chown mysql:mysql /var/run/mysql**

4. Inicie o serviço: ***$ mysql -u root***
5. Agora iremos mudar a senha:
> mysql> **use mysql;**
mysql> **update user set authentication_string=PASSWORD("SuaSenha") where User='root';**
mysql> **update user set plugin="mysql_native_password";**
mysql> **flush privileges;**
mysql> **quit;**

6. Reinicie a maquina.

