# Random Repository

This repository contains various projects and utilities.

## Projects

### Employee Management and Payroll System (xyzz/)

A comprehensive employee management and payroll system built using Java, Maven, JDBC, and MySQL.

**📋 Documentation:**
- **[Complete Project Report](xyzz/PROJECT_REPORT.md)** - Comprehensive 1,735-line project documentation
- [README](xyzz/README.md) - User guide and setup instructions
- [Quick Start Guide](xyzz/QUICKSTART.md) - 5-minute setup guide
- [Implementation Summary](xyzz/IMPLEMENTATION_SUMMARY.md) - Technical architecture overview
- [Menu Guide](xyzz/MENU_GUIDE.md) - User interface reference

**Key Features:**
- Employee lifecycle management (CRUD operations)
- Automated payroll generation and processing
- Department management
- Comprehensive reporting system
- Database-driven with MySQL
- Console-based user interface

**Technology Stack:**
- Java 17
- Apache Maven
- JDBC (MySQL Connector)
- MySQL 8.0

**Quick Start:**
```bash
cd xyzz
mysql -u root -p < src/main/resources/schema.sql
# Edit src/main/resources/db.properties with your MySQL credentials
mvn clean package
java -jar target/employee-management-payroll-1.0-SNAPSHOT.jar
```

For complete details, see the [Project Report](xyzz/PROJECT_REPORT.md).
