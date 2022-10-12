### Install DB (MariaDB)
1) With homebrew `brew install mariadb`
2) To manage it (Start, stop and restart) `brew services restart mariadb`

### To create new db user
1) Type in the terminal `mysql` 
2) Create user `CREATE USER 'user1'@localhost IDENTIFIED BY 'password1';`
3) To assure the user is added `SELECT User FROM mysql.user;`
4) Grant all privileges `GRANT ALL PRIVILEGES ON *.* TO 'user1'@localhost;`
5) Flush all the privileges `FLUSH PRIVILEGES;`

### Download any db mamnagement tool or even script like adminer
- Now easily you can login with your credentials