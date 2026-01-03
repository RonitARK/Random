# Employee Management System - Menu Structure

## Application Flow Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│     EMPLOYEE MANAGEMENT & PAYROLL SYSTEM                        │
│     Java + Maven + JDBC + MySQL                                 │
└─────────────────────────────────────────────────────────────────┘
                            │
                            ▼
        ┌───────────────────────────────────────┐
        │          MAIN MENU                    │
        ├───────────────────────────────────────┤
        │  1. Employee Management               │
        │  2. Payroll Management                │
        │  3. Department Management             │
        │  4. Reports                           │
        │  5. Exit                              │
        └───────────────────────────────────────┘
                │           │           │           │
    ┌───────────┘           │           │           └───────────┐
    ▼                       ▼           ▼                       ▼
┌────────────────┐  ┌────────────────┐  ┌────────────────┐  ┌────────────────┐
│   EMPLOYEE     │  │    PAYROLL     │  │  DEPARTMENT    │  │    REPORTS     │
│  MANAGEMENT    │  │  MANAGEMENT    │  │  MANAGEMENT    │  │                │
├────────────────┤  ├────────────────┤  ├────────────────┤  ├────────────────┤
│ 1. Add New     │  │ 1. Generate    │  │ 1. Add New     │  │ 1. All         │
│    Employee    │  │    Payroll     │  │    Department  │  │    Employees   │
│                │  │    (Individual)│  │                │  │                │
│ 2. View All    │  │                │  │ 2. View All    │  │ 2. All Payroll │
│    Employees   │  │ 2. View All    │  │    Departments │  │    Records     │
│                │  │    Payroll     │  │                │  │                │
│ 3. Search      │  │    Records     │  │ 3. Update      │  │ 3. Dept-wise   │
│    Employee    │  │                │  │    Department  │  │    Employee    │
│                │  │ 3. View        │  │                │  │    Count       │
│ 4. Update      │  │    Employee    │  │ 4. Delete      │  │                │
│    Employee    │  │    Payroll     │  │    Department  │  │ 4. Employee    │
│                │  │    History     │  │                │  │    Payroll     │
│ 5. Delete      │  │                │  │ 5. Back        │  │    Summary     │
│    Employee    │  │ 4. Process     │  │                │  │                │
│                │  │    Payment     │  └────────────────┘  └────────────────┘
│ 6. View by     │  │                │
│    Department  │  │ 5. Generate    │
│                │  │    Monthly     │
│ 7. Back        │  │    Payroll     │
│                │  │    (All Emps)  │
└────────────────┘  │                │
                    │ 6. Update      │
                    │    Payroll     │
                    │                │
                    │ 7. Delete      │
                    │    Payroll     │
                    │                │
                    │ 8. Back        │
                    └────────────────┘
```

## User Interaction Flow Examples

### Example 1: Adding an Employee

```
Main Menu → 1. Employee Management
          → 1. Add New Employee
          → [Enter employee details]
          → ✓ Employee added successfully!
          → [Return to Employee Management Menu]
```

### Example 2: Generating Payroll

```
Main Menu → 2. Payroll Management
          → 1. Generate Payroll for Employee
          → [Enter Employee ID]
          → [System displays employee info and salary]
          → [Enter pay period dates]
          → [Enter bonus and deductions]
          → ✓ Payroll generated successfully!
          → [Display calculated net salary]
          → [Return to Payroll Management Menu]
```

### Example 3: Processing Payment

```
Main Menu → 2. Payroll Management
          → 4. Process Payment
          → [Enter Payroll ID]
          → [System displays payroll details]
          → [Confirm payment: yes/no]
          → ✓ Payment processed successfully!
          → [Status updated to PAID with current date]
          → [Return to Payroll Management Menu]
```

### Example 4: Viewing Reports

```
Main Menu → 4. Reports
          → 1. All Employees Report
          → [System displays formatted table of all employees]
          → [Shows: ID, Name, Email, Phone, Hire Date, Title, Dept, Salary]
          → [Return to Main Menu]
```

## Data Flow

```
User Input → Presentation Layer (EmployeeManagementApp)
              │
              ▼
           Service Layer (Validation & Business Logic)
              │
              ▼
           DAO Layer (Database Operations)
              │
              ▼
           JDBC Connection (DatabaseConnection Utility)
              │
              ▼
           MySQL Database (employee_payroll_db)
              │
              ▼
           [Data Retrieved/Modified]
              │
              ▼
           Display Results to User
```

## Key Operations with Input/Output

### 1. Add Employee
```
INPUT:
- First Name: John
- Last Name: Doe
- Email: john.doe@company.com
- Phone: 555-1234
- Hire Date: 2024-01-15
- Job Title: Software Engineer
- Department ID: 2
- Salary: 75000

OUTPUT:
✓ Employee added successfully! Employee ID: 6
```

### 2. Generate Payroll
```
INPUT:
- Employee ID: 1
- Pay Period Start: 2024-01-01
- Pay Period End: 2024-01-31
- Bonus: 1000.00
- Deductions: 500.00

CALCULATION:
Basic Salary: $75,000.00
Bonus: $1,000.00
Deductions: $500.00
Net Salary: $75,500.00

OUTPUT:
✓ Payroll generated successfully!
Net Salary: $75,500.00
```

### 3. View All Employees (Sample Output)
```
════════════════════════════════════════════════════════════════════════════
ID    First Name    Last Name     Email                    Phone         ...
════════════════════════════════════════════════════════════════════════════
1     John          Doe           john.doe@company.com     123-456-7890  ...
2     Jane          Smith         jane.smith@company.com   123-456-7891  ...
3     Bob           Johnson       bob.johnson@company.com  123-456-7892  ...
════════════════════════════════════════════════════════════════════════════
```

### 4. Employee Payroll Summary (Sample Output)
```
===== Payroll Summary for John Doe =====
Total Payroll Records: 12
Total Paid: $75,500.00
Total Pending: $25,000.00
═══════════════════════════════════════
```

## Error Handling Examples

### Invalid Input
```
Enter your choice: abc
❌ Invalid input. Please enter a number.
```

### Employee Not Found
```
Enter Employee ID: 999
❌ Employee not found.
```

### Database Connection Failed
```
⚠ WARNING: Database connection failed!
Please ensure MySQL is running and database is configured correctly.
```

### Validation Error
```
❌ Error: Email is required
❌ Error: Salary must be greater than 0
❌ Error: Pay period start date must be before end date
```

## Navigation Tips

1. **Always read the menu carefully** before selecting an option
2. **Enter exact numbers** for menu choices (1, 2, 3, etc.)
3. **Use yyyy-MM-dd format** for all dates (e.g., 2024-01-15)
4. **Confirm deletions** - system will ask for confirmation
5. **Press Enter** to skip optional fields during updates
6. **Use descriptive searches** - partial name matching is supported

## System Responses

- ✓ Success messages are prefixed with checkmark
- ❌ Error messages are prefixed with X
- ⚠ Warning messages are prefixed with warning symbol
- Formatted tables use borders for clarity
- Calculations are shown before final confirmation

---

This menu structure provides a complete, user-friendly interface for managing employees and payroll efficiently!
