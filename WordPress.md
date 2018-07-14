To setup Wordpress:

1. `mysql -u root -p`
2. `create database wordpressdb;`
3. `create user 'wpuser'@'localhost' identified by 'wordpress-pw';`
4. `grant all privileges on wordpressdb.* to 'wpuser'@'localhost'`;
5. `flush privileges;`
6. `exit`
7. `wget https://wordpress.org/latest.tar.gz`
8. `tar xzf latest.tar.gz`
9. `cd wordpress`
10. `cp wp-config-sample.php wp-config.php`
11. `vim wp-config.php`
    * `wordpressdb`
    * `wpuser`
    * `wordpress-pw`
    * Copy/paste the salts from the [wordpress site](https://api.wordpress.org/secret-key/1.1/salt/) into the config file
12. `sudo rm /var/www/html/index.html`
13. `cp -r * /var/www/html`
14. `https://my-public-dns.com/wp-admin/install.php`

### Migrating to RDS

1. Dump your database: `mysqldump -u wpuser -p wordpressdb > /home/ubuntu/backup.sql`
2. Create an RDS instance
    * Username/password must match!
3. Upload your dump 
    * SSH to EC2, use the URL for your database
    * `mysql -u wpuser -p --database=wordpressdb --host=db.some-address.com < backup.sql`
4. Change `DB_HOST` to new RDS URL
