# Employee Management System - Quick Start Guide

## System Overview

This is a comprehensive Employee Management and Payroll System built with:
- **Java 17** - Core programming language
- **Maven** - Dependency management and build tool
- **JDBC** - Database connectivity layer
- **MySQL 8.0** - Relational database

## Quick Start (5 Minutes)

### Step 1: Database Setup
```bash
# Login to MySQL
mysql -u root -p

# Create and initialize the database
source src/main/resources/schema.sql

# Exit MySQL
exit;
```

### Step 2: Configure Database Connection
Edit `src/main/resources/db.properties`:
```properties
db.url=jdbc:mysql://localhost:3306/employee_payroll_db
db.username=root
db.password=YOUR_PASSWORD_HERE
db.driver=com.mysql.cj.jdbc.Driver
```

### Step 3: Build and Run
```bash
# Build the project
mvn clean package

# Run the application
java -jar target/employee-management-payroll-1.0-SNAPSHOT.jar
```

## Features at a Glance

### 1. Employee Management
- ✅ Add new employees
- ✅ View all employees
- ✅ Search employees by name
- ✅ Update employee information
- ✅ Delete employees
- ✅ Filter employees by department

### 2. Payroll Management
- ✅ Generate payroll for individual employees
- ✅ Generate monthly payroll for all employees
- ✅ View payroll history
- ✅ Process payments
- ✅ Track bonuses and deductions
- ✅ Automatic net salary calculation

### 3. Department Management
- ✅ Create departments
- ✅ View all departments
- ✅ Update department information
- ✅ Delete departments

### 4. Reporting
- ✅ Employee reports
- ✅ Payroll reports
- ✅ Department-wise employee count
- ✅ Individual employee payroll summary

## Usage Examples

### Adding an Employee
1. Select "1. Employee Management" from main menu
2. Select "1. Add New Employee"
3. Enter employee details:
   ```
   First Name: John
   Last Name: Doe
   Email: john.doe@company.com
   Phone: 555-1234
   Hire Date: 2024-01-15
   Job Title: Software Engineer
   Department ID: 2
   Salary: 75000
   ```

### Generating Payroll
1. Select "2. Payroll Management" from main menu
2. Select "1. Generate Payroll for Employee"
3. Enter:
   ```
   Employee ID: 1
   Pay Period Start: 2024-01-01
   Pay Period End: 2024-01-31
   Bonus: 1000
   Deductions: 500
   ```
4. System calculates net salary automatically

### Processing Payment
1. Select "2. Payroll Management"
2. Select "4. Process Payment"
3. Enter Payroll ID
4. Confirm payment
5. Status updates to "PAID" with current date

## Database Schema

The system uses three main tables:

### employees
Stores employee information including personal details, job title, department, and salary.

### payroll
Tracks all payroll records with pay periods, bonuses, deductions, and payment status.

### departments
Manages organizational departments.

## Troubleshooting

### Connection Failed
- Ensure MySQL is running: `sudo systemctl status mysql`
- Check credentials in `db.properties`
- Verify database exists: `SHOW DATABASES;`

### Build Failed
- Check Java version: `java -version` (must be 17+)
- Check Maven version: `mvn -version` (must be 3.6+)
- Clear Maven cache: `mvn clean`

### Application Won't Start
- Verify JAR file exists in `target/` directory
- Check that db.properties has correct credentials
- Ensure MySQL is accepting connections on port 3306

## Sample Data

The system comes with pre-populated sample data:
- 5 departments (HR, Engineering, Finance, Marketing, Operations)
- 5 sample employees
- Ready to test all features immediately

## Command Reference

```bash
# Build only
mvn compile

# Build and package
mvn package

# Clean build artifacts
mvn clean

# Run with Maven
mvn exec:java -Dexec.mainClass="com.employee.management.EmployeeManagementApp"

# Run JAR directly
java -jar target/employee-management-payroll-1.0-SNAPSHOT.jar

# Run with dependencies
java -cp "target/*:target/lib/*" com.employee.management.EmployeeManagementApp
```

## Project Structure

```
xyzz/
├── pom.xml                      # Maven configuration
├── README.md                    # Full documentation
├── QUICKSTART.md               # This file
├── setup.sh                    # Setup automation script
└── src/
    ├── main/
    │   ├── java/               # Source code
    │   │   └── com/employee/management/
    │   │       ├── EmployeeManagementApp.java
    │   │       ├── model/      # Entity classes
    │   │       ├── dao/        # Database operations
    │   │       ├── service/    # Business logic
    │   │       └── util/       # Utilities
    │   └── resources/
    │       ├── db.properties   # Database config
    │       └── schema.sql      # Database schema
    └── test/
        └── java/               # Test files
```

## Next Steps

1. Explore all menu options
2. Add your own employees
3. Generate payroll records
4. View reports
5. Customize the system for your needs

## Support

For issues or questions:
- Check the main README.md for detailed documentation
- Review the source code comments
- Examine the SQL schema in `src/main/resources/schema.sql`

## Tips

- Date format must be: yyyy-MM-dd (e.g., 2024-01-15)
- Always confirm database backups before deletions
- Use department IDs when assigning employees
- Net salary is calculated automatically (basic + bonus - deductions)
- Payment processing marks status as "PAID" and records the date

---

**Built with Java, Maven, JDBC, and MySQL**
