# GameVault: Interactive Database Management System

## Project Overview
This web application provides an interface for interacting with a game database. It allows users to view, filter, and update game-related data through a simple JSP web interface.


## Features
The application supports the following core operations:

1. **List-Based Report**
   - Displays a summary of game entities with meaningful attributes
   - Supports filtering on user-friendly attributes with partial matching
   - Displays human-readable values rather than synthetic keys
   - Each item links to a detailed report
   - Items are sorted in a meaningful way

2. **Detail Report**
   - Accessed by clicking on items in the list report
   - Shows comprehensive information by combining data from at least three different tables
   - Includes both summary data and additional detailed information
   - Avoids displaying synthetic keys to users

3. **Update Functionality**
   - Allows users to update non-enumeration table data
   - Accessible via link/button from the detail report
   - Implements proper SQL injection protection

## Technical Implementation

### Database Components
- MySQL database
- Tables with at least 10 sample records each
- Properly defined enumeration tables

### Application Structure
- **Model Classes**: Java classes representing database entities
- **DAO Classes**: Data Access Objects for database operations
- **JSP Files**: Web pages for user interface
- **Servlet Classes**: Controllers implementing web page behavior
- **SQL File**: Database creation and population script

### Security
All database operations include protection against SQL injection attacks using prepared statements.

## Setup Instructions

### Prerequisites
- Java Development Kit (JDK) 8 or higher
- Apache Tomcat 9
- MySQL Server 8.0 or higher
- Maven (optional, if using for dependency management)

### Database Setup
1. Log in to MySQL:
   ```
   mysql -u [username] -p
   ```
2. Create a new database:
   ```
   CREATE DATABASE game_db;
   USE game_db;
   ```
3. Run the SQL script to create and populate tables:
   ```
   source [path_to_sql_file]
   ```

### Application Deployment
1. Clone the repository or unzip the project files
2. Configure the database connection in `[connection_config_file]`
3. Build the project (if using Maven):
   ```
   mvn clean package
   ```
4. Deploy the WAR file to Tomcat:
   - Copy the WAR file to Tomcat's `webapps` directory
   - Start Tomcat: `[tomcat_dir]/bin/startup.sh` (or `.bat` for Windows)
5. Access the application at: `http://localhost:8080/[app_name]`

## Usage Guide

### Viewing the List Report
1. Navigate to the home page
2. Use the filter field to search for specific games by [filter_attribute]
3. Click on any game in the list to view detailed information

### Viewing Detailed Information
1. From the list report, click on a game title
2. View comprehensive information about the selected game
3. Use the navigation options to return to the list or update the game

### Updating Game Information
1. From the detail view, click the "Update" button
2. Modify the desired fields in the form
3. Submit the form to save changes
4. View the updated game details

## Project Structure
```
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   ├── models/       # Entity model classes
│   │   │   ├── dao/          # Data Access Objects
│   │   │   └── servlets/     # Controller servlets
│   │   ├── webapp/
│   │   │   ├── WEB-INF/
│   │   │   │   └── web.xml   # Web application configuration
│   │   │   ├── css/          # Stylesheets
│   │   │   └── *.jsp         # JSP pages
│   │   └── resources/
│   │       └── *.properties  # Configuration files
│   └── test/                 # Test classes (if applicable)
├── sql/
│   └── game_db.sql           # Database creation and population script
├── pom.xml                   # Maven configuration (if applicable)
└── README.md                 # This file
```
