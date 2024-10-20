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
