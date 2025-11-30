# Clash of Clans (COC) Database Management System

[![Database Project](https://img.shields.io/badge/Database-MySQL-blue)](https://www.mysql.com/)
[![Python](https://img.shields.io/badge/Language-Python-green)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-Academic-blueviolet)](LICENSE)

A comprehensive database management system for Clash of Clans game data, designed to efficiently store, retrieve, and manage all aspects of the game including players, clans, battles, troops, spells, heroes, and more.

## 📋 Table of Contents
- [Project Overview](#project-overview)
- [Features and Functionality](#features-and-functionality)
- [Database Schema](#database-schema)
- [Installation](#installation)
- [Setup](#setup)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Team](#team)


## 📖 Project Overview

This project implements a Clash of Clans (COC) database management system that provides comprehensive data handling for the popular mobile game. The system enables efficient querying, data management, and analysis of game-related information. This academic project demonstrates practical application of database design principles, normalization, SQL queries, and database connectivity using Python.

### 🛠️ Technologies Used
- **Database**: MySQL 8.0+
- **Backend Language**: Python 3.x
- **Database Connector**: PyMySQL
- **CLI Interface**: Custom Python implementation
- **Data Visualization**: PrettyTable for formatted output
- **Design Tool**: Draw.io for ER diagrams

### 🎯 Purpose
- Demonstrate database normalization principles (1NF, 2NF, 3NF)
- Implement complex SQL queries for real-world scenarios
- Provide efficient data management for game entities
- Create an intuitive command-line interface for database operations

## ⚡ Features and Functionality

The COC Database Management System provides 16 essential operations:

1. **Retrieve Opponents**: Get a list of all opponents faced by a specific player
2. **Max Hitpoints Defense**: Find the defense with maximum hitpoints
3. **League Players**: Retrieve names of players in a specific league
4. **Clan Members**: Retrieve names of all members of a clan
5. **Clan Win-Lose Ratio**: Calculate the highest win-lose ratio of a clan
6. **Average Clan Medals**: Calculate the average medals of a clan
7. **Clan Search**: Search for clan names containing the string 'War'
8. **Player Search**: Search for player names starting with the alphabet 'U'
9. **New Player**: Add details of a new player joining the game
10. **New Troop**: Add details of a new troop added to the game
11. **Player Upgrade**: Update a player's Town Hall level after an upgrade
12. **Trophy Update**: Update trophy count of a player after a battle
13. **Clan Deletion**: Delete details of a clan with zero members
14. **Troop Deletion**: Delete details of a troop removed from the game
15. **Attack Timing Analysis**: Investigate how attack timing is affected at a particular Town Hall
16. **Popularity Analysis**: Analyze the popularity of troops, spells, and heroes

## 🗄️ Database Schema

The system is built on a normalized relational database with the following main entities:

### Core Entities:
- **Player**: Stores player information including ID, name, resources, and stats
- **Clan**: Manages clan information including members, medals, and战绩
- **Leagues**: Defines league categories with trophy ranges
- **Troops**: Contains all troop types with their properties (hitpoints, damage, training time, etc.)
- **Spells**: Stores spell information and attributes
- **Heroes**: Manages hero data with unique abilities
- **Defences**: Details defensive structures in the game (hitpoints, damage, range, etc.)
- **Buildings**: Contains building information

### Relationship Tables:
- **Players_Attack_Log**: Tracks all battles between players
- **Player_part_of_clan**: Manages player-clan relationships
- **ClanWar**: Records clan versus clan battles
- **PlayersAchievements**: Tracks player achievements
- **Army Composition Tables**: Manages troop, spell, and hero combinations

### Normalization
- **1NF**: Eliminated multi-valued attributes by creating separate relationship tables
- **2NF**: Ensured partial dependencies are addressed with proper primary keys
- **3NF**: Eliminated transitive dependencies across all relations

## 🚀 Installation

### Prerequisites
- Python 3.6 or higher
- MySQL Server 8.0 or higher
- pip (Python package manager)

### Installation Steps

1. **Clone the repository** (if available):
   ```bash
   git clone <repository-url>
   cd COC-DBMS
   ```

2. **Install Python dependencies**:
   ```bash
   pip install pymysql prettytable
   ```

   Or if you have a requirements.txt file:
   ```bash
   pip install -r requirements.txt
   ```

3. **Start MySQL Server**:
   ```bash
   sudo service mysql start
   # or depending on your system:
   sudo systemctl start mysql
   # On macOS with Homebrew:
   brew services start mysql
   # On Windows:
   net start mysql
   ```

## ⚙️ Setup

### Database Initialization

1. **Open MySQL command line**:
   ```bash
   mysql -u root -p
   ```

2. **Create Database User** (execute the setup.sql file):
   ```bash
   # In a separate terminal (don't exit MySQL)
   mysql -u root -p < "COC Database/setup.sql"
   ```

   Or execute manually in MySQL:
   ```sql
   CREATE USER 'bruh'@'localhost' IDENTIFIED BY 'Password@123';
   GRANT ALL PRIVILEGES ON *.* TO 'bruh'@'localhost';
   FLUSH PRIVILEGES;
   ```

3. **Create Database and Tables**:
   ```bash
   mysql -u root -p < "COC Database/database.sql"
   ```

4. **Verify Setup**:
   ```bash
   mysql -u bruh -p
   # Use password: Password@123
   SHOW DATABASES;
   USE COC_Database;
   SHOW TABLES;
   ```

## 🎮 Usage

### Running the Application

1. **Navigate to the source directory**:
   ```bash
   cd "COC Database/source_code/"
   ```

2. **Run the Python CLI application**:
   ```bash
   python dna_sql_pythoncli.py
   ```

3. **Follow the on-screen menu to select desired functionality**:
   - The application will display a menu of 16 available operations
   - Enter the query number (1-16) to execute the corresponding operation
   - For operations requiring input, enter the requested information
   - Results will be displayed in a formatted table

### Example Usage Scenarios

1. **Viewing Opponents**:
   - Select option "1"
   - Enter the Player ID you want to query
   - The system will return all opponents that player has faced

2. **Adding a New Player**:
   - Select option "9"
   - Enter a unique Player ID (format: P###)
   - Enter the Player Name
   - The system will add the new player to the database

3. **Finding Maximum Hitpoints Defense**:
   - Select option "2"
   - The system will display the defense with the highest hitpoints

4. **Clan Search**:
   - Select option "7"
   - The system will display all clans with "War" in their name

5. **Analyzing Popularity**:
   - Select option "16"
   - The system will analyze and display the most popular troops, spells, and heroes

### Troubleshooting

- **Connection Error**: Ensure MySQL server is running and the user credentials are correct
- **Permission Error**: Verify that the 'bruh' user has been created with the correct password
- **File Path Issues**: Ensure you're in the correct directory when executing commands

## 📁 Project Structure

```
COC-DBMS/
├── README.md
├── COC Database/
│   ├── database.sql          # Main database schema and sample data
│   ├── setup.sql             # Database user setup script
│   ├── Diagrams.pdf          # ER diagrams and normalization documentation
│   ├── Report.pdf            # Detailed project report
│   └── source_code/
│       └── dna_sql_pythoncli.py  # Main Python CLI application
```

### Key Files:
- **database.sql**: Complete database schema with all tables, relationships, and sample data
- **setup.sql**: Creates the required database user and grants permissions
- **dna_sql_pythoncli.py**: Main application with all 16 database operations
- **Diagrams.pdf**: Database design documentation with unnormalized and normalized schemas
- **Report.pdf**: Phase 4 documentation with detailed query explanations

## 👥 Team

**Group 14 - SQ(L)uad**
- Academic Project for Database Management Systems Course

## 📄 License

This project is an academic assignment for Database Management Systems course. The code and documentation are intended for educational purposes.

---




