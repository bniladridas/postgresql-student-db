# 🎓 PostgreSQL Student Database Project

A database management system built with PostgreSQL and Bash scripting to manage computer science students' information, developed as part of the freeCodeCamp Relational Database certification.

## 📋 Project Overview

This project implements a student database using PostgreSQL and Bash scripting. It includes functionality to load student and course data from CSV files into a PostgreSQL database using SQL commands.

### 🔑 Key Features

- Data import from CSV files
- Automated database population
- SQL table creation and management
- Bash script automation
- Student and course information management

## 🛠️ Project Structure

```
postgresql-student-db/
├── README.md
├── students.sql         # SQL commands for creating database structure
├── insert_data.sh      # Bash script for importing data
├── students.csv        # Student information data
├── courses.csv         # Course information data
└── docs/
    └── setup_guide.md
```

## 🚀 Getting Started

### Prerequisites

- PostgreSQL installed on your system
- Git
- Bash terminal
- Access to command line

### Installation

1. Clone the repository
```bash
git clone https://github.com/bniladridas/postgresql-student-db
cd postgresql-student-db
```

2. Set up the database structure
```bash
psql -U postgres < students.sql
```

3. Make the insertion script executable
```bash
chmod +x insert_data.sh
```

4. Run the data insertion script
```bash
./insert_data.sh
```

## 💡 Usage

### Database Setup
The `students.sql` file contains all necessary SQL commands to:
- Create the database structure
- Set up required tables
- Define relationships between tables

### Data Import
The `insert_data.sh` script automatically:
- Reads data from `students.csv` and `courses.csv`
- Processes the data for database insertion
- Populates the database tables

### Data Files
- `students.csv`: Contains student information
- `courses.csv`: Contains course information

## 📊 Database Schema

The database includes tables for:
- Students information
- Course details
- Related academic data

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👏 Acknowledgments

- freeCodeCamp for providing the project requirements and structure
- PostgreSQL documentation
- The open-source community

## 📧 Contact

Niladri Das - [dasniladri874@gmail.com](mailto:dasniladri874@gmail.com)

Project Link: [https://github.com/bniladridas/postgresql-student-db](https://github.com/bniladridas/postgresql-student-db)