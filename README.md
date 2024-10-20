
# AWS EC2 LEMP Stack Setup (Nginx, MariaDB, PHP-FPM)

## Project Description
This project sets up a complete LEMP (Linux, Nginx, MariaDB, PHP) stack on an AWS EC2 Ubuntu instance. It demonstrates how to configure a server to host dynamic websites using Nginx, manage databases with MariaDB, and process PHP files with PHP-FPM and PHP-MySQL.

---

## Features

- Hosting a dynamic website with Nginx.
- Database management with MariaDB.
- PHP processing using PHP-FPM and PHP-MySQL.
- AWS EC2 setup for scalable cloud infrastructure.
- Successfully tested with `info.php` to verify PHP configuration.

---

## Installation

### Prerequisites:

1. AWS EC2 Ubuntu instance.
2. Nginx, MariaDB, PHP-FPM, and PHP-MySQL installed on the server.
3. SSH access to your EC2 instance.

### Steps:

1. **Update and Upgrade Your Server:**
   ```bash
   sudo apt update && sudo apt upgrade
   ```

2. **Install Nginx:**
   ```bash
   sudo apt install nginx
   ```
   - Start and enable Nginx:
   ```bash
   sudo systemctl start nginx
   sudo systemctl enable nginx
   ```

3. **Install MariaDB:**
   ```bash
   sudo apt install mariadb-server mariadb-client
   ```
   - Secure MariaDB installation:
   ```bash
   sudo mysql_secure_installation
   ```

4. **Install PHP, PHP-FPM, and PHP-MySQL:**
   ```bash
   sudo apt install php-fpm php-mysql
   ```

5. **Configure Nginx to Use PHP-FPM:**
   - Open the default Nginx server block:
   ```bash
   sudo nano /etc/nginx/sites-available/default
   ```
   - Modify the configuration to process PHP files by updating the `location ~ \.php$` block:
   ```nginx
   location ~ \.php$ {
       include snippets/fastcgi-php.conf;
       fastcgi_pass unix:/run/php/php7.4-fpm.sock; # Adjust if using a different PHP version
   }
   ```
   - Save the file and exit.

6. **Restart Nginx and PHP-FPM:**
   ```bash
   sudo systemctl restart nginx
   sudo systemctl restart php7.4-fpm  # Or your installed PHP version
   ```

7. **Test PHP with info.php:**
   - Create a test file to ensure PHP is working:
   ```bash
   sudo nano /var/www/html/info.php
   ```
   - Add the following content:
   ```php
   <?php
   phpinfo();
   ?>
   ```
   - Save and exit.

8. **Access the Test Page:**
   - Open your web browser and go to `http://your-ec2-public-ip/info.php`. If everything is set up correctly, you should see the PHP information page.

9. **Set Up MariaDB Database:**
   - Log in to MariaDB:
   ```bash
   sudo mysql -u root -p
   ```
   - Create a database and user:
   ```sql
   CREATE DATABASE yourdbname;
   CREATE USER 'youruser'@'localhost' IDENTIFIED BY 'yourpassword';
   GRANT ALL PRIVILEGES ON yourdbname.* TO 'youruser'@'localhost';
   FLUSH PRIVILEGES;
   ```

---

## Usage

1. **Server Access:**  
   Access your web server by navigating to `http://your-ec2-public-ip` or `http://your-domain.com` if youâ€™ve set up a domain.

2. **Database Management:**  
   Manage your MariaDB databases through the command line or using tools like phpMyAdmin.

3. **PHP Testing:**  
   Ensure PHP works correctly by testing with the `info.php` file.

4. **Remove info.php (for security):**  
   Once tested, remove the file for security purposes:
   ```bash
   sudo rm /var/www/html/info.php
   ```

---

## License

This project is licensed under the MIT License. See the LICENSE file for more details.

---

## Contact

For any issues or queries, feel free to reach out:

- **Email:** vivek@yourdomain.com
- **GitHub:** [GitHub Profile](https://github.com/yourusername)
