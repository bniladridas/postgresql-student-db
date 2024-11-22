# 📚 Student Database Setup Guide

This comprehensive guide will walk you through setting up and configuring the PostgreSQL Student Database Manager on your system.

## Table of Contents
- [System Requirements](#system-requirements)
- [Installation Steps](#installation-steps)
- [Database Configuration](#database-configuration)
- [Troubleshooting](#troubleshooting)
- [Additional Configuration](#additional-configuration)

## System Requirements

### Minimum Requirements
- Operating System: Linux, macOS, or Windows with WSL
- RAM: 2GB (4GB recommended)
- Storage: 1GB free space
- PostgreSQL 12.0 or higher
- Bash shell
- Git

### Software Dependencies
```bash
# Ubuntu/Debian
sudo apt-get update
sudo apt-get install -y postgresql postgresql-contrib git

# macOS (using Homebrew)
brew install postgresql git

# Windows
# Install WSL2 and Ubuntu, then follow Ubuntu instructions
```

## Installation Steps

### 1. PostgreSQL Installation Verification
```bash
# Check PostgreSQL installation
psql --version

# Start PostgreSQL service
# On Linux
sudo systemctl start postgresql
sudo systemctl enable postgresql

# On macOS
brew services start postgresql
```

### 2. Project Setup
```bash
# Clone the repository
git clone https://github.com/your-username/postgresql-student-db
cd postgresql-student-db

# Set up database user and permissions
sudo -u postgres createuser --interactive
# When prompted:
# Enter name of role to add: student_db_user
# Shall the new role be a superuser? n
# Shall the new role be allowed to create databases? y
# Shall the new role be allowed to create more new roles? n

# Create database
sudo -u postgres createdb student_db

# Set user password
sudo -u postgres psql
postgres=# ALTER USER student_db_user WITH PASSWORD 'your_password';
postgres=# \q
```

### 3. Database Configuration

#### Configure PostgreSQL Authentication
Edit the PostgreSQL configuration file:
```bash
# Linux
sudo nano /etc/postgresql/[version]/main/pg_hba.conf

# macOS
nano /usr/local/var/postgres/pg_hba.conf
```

Add the following line:
```
local   student_db   student_db_user   md5
```

#### Initialize Database Schema
```bash
# Run the database setup script
psql -U student_db_user -d student_db -f database_setup.sql
```

## Troubleshooting

### Common Issues and Solutions

1. **Connection Refused**
```bash
# Check if PostgreSQL is running
sudo systemctl status postgresql

# Restart PostgreSQL
sudo systemctl restart postgresql
```

2. **Permission Denied**
```bash
# Grant necessary permissions
sudo chown postgres:postgres /var/run/postgresql

# Verify file permissions
ls -la /var/run/postgresql
```

3. **Database Already Exists**
```bash
# Drop and recreate database
sudo -u postgres dropdb student_db
sudo -u postgres createdb student_db
```

## Additional Configuration

### Environment Variables
Create a `.env` file in the project root:
```bash
DB_HOST=localhost
DB_PORT=5432
DB_NAME=student_db
DB_USER=student_db_user
DB_PASSWORD=your_password
```

### Script Permissions
```bash
# Make scripts executable
chmod +x *.sh

# Set correct ownership
chown -R $USER:$USER .
```

### Backup Configuration
```bash
# Create backup directory
mkdir -p backups

# Set up automated backups (optional)
# Add to crontab
0 0 * * * /path/to/backup_script.sh
```

## Testing the Installation

1. Test database connection:
```bash
psql -U student_db_user -d student_db -c "\l"
```

2. Run the test script:
```bash
./test_connection.sh
```

3. Verify the installation:
```bash
# Check if tables were created
psql -U student_db_user -d student_db -c "\dt"
```

## Next Steps

After completing the setup:
1. Review the main README.md for usage instructions
2. Run a test query to verify the setup
3. Start adding student data through the CLI interface

For additional help or troubleshooting, please:
- Check the project's issue tracker
- Review PostgreSQL logs (`/var/log/postgresql/postgresql-[version]-main.log`)
- Contact the project maintainers

## Security Notes

1. Always change default passwords
2. Regularly update PostgreSQL to the latest version
3. Back up your database regularly
4. Keep your `.env` file secure and never commit it to version control

## Updates and Maintenance

To update the application:
```bash
git pull origin main
./update_schema.sh
```

Remember to back up your data before performing any updates or maintenance.