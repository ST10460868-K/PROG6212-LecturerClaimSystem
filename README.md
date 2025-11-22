# 📚 Lecturer Monthly Claim System
## ASP.NET Core MVC - Automated Verification & Approval System

### 🎯 Project Overview

The Lecturer Monthly Claim System is a full-stack ASP.NET Core MVC web application that automates the submission, validation, approval, and processing of monthly lecturer claims.

The system ensures accuracy through auto-calculation, strict business rule validation, automated approval (for claims under R5,000), and a professional, user-friendly interface. It supports both lecturer submissions and coordinator/manager workflows.
---

# ✨ Key Features
## ✅ 1. Automated Verification & Approval

- Auto-calculation of claim totals

- Real-time validation (client + server)

- Auto-approval for claims ≤ R5,000

- Business rule validation

- Smart error handling

- Inline validation summary

- Automatic workflow movement

---

## ✅ 2. Claim Processing Automation

- Automated claim status transitions:
Submitted → InReview → Approved/Rejected → Processed

- Bulk approval for Programme Coordinators

- Role-specific permissions

- Entity Framework Core data handling

- Secure file uploads (PDF/DOCX/JPG/PNG)

---

## ✅ 3. Professional GUI (High Marks)

- Gradient tech theme (purple/blue modern UI)

- Bootstrap 5 + Custom CSS

- Icons integrated (FontAwesome/Lucide style)

- Fully responsive

- Card-based dashboards

- Clean data tables

- User-friendly forms

---

## ✅ 4. User-Friendly Experience

- Auto-calc of totals as user types

- Instant validation feedback

- Document upload previews

- Clear navigation per role
 
- Progress visibility in every dashboard

---

## 🛠️ Technology Stack

| Component      | Technology                             |
| -------------- | -------------------------------------- |
| Framework      | **ASP.NET Core MVC 9.0**               |
| Database       | **Entity Framework Core + SQL Server** |
| Authentication | **ASP.NET Identity**                   |
| Validation     | **FluentValidation**                   |
| Workflow       | Custom role-based approvals            |
| Reporting      | Razor Pages views for summaries        |

---

## 📦 Project Structure

```
ContractMonthlyClaimSystem/
├── Controllers/
│   ├── DashboardController.cs         # Handles dashboards for Lecturer, PC, PM, HR
│   ├── AccountController.cs (optional) # Login & role management
│   └── ReportController.cs (optional)  # Report generation
│
├── Models/
│   ├── Claim.cs                       # Main claim model
│   ├── ApplicationUser.cs             # Identity user with roles
│   └── RoleSetup.cs                   # Role creation and seeding
│
├── Data/
│   └── ApplicationDbContext.cs        # EF Core DB context
│
├── Views/
│   ├── Account/
│   │   └── Login.cshtml               # Login modal / login screen
│   │
│   ├── Lecturer/
│   │   ├── Dashboard.cshtml           # Lecturer dashboard view
│   │   └── CreateClaim.cshtml         # Claim submission form (if included)
│   │
│   ├── ProgrammeCoordinator/
│   │   └── Dashboard.cshtml           # PC Dashboard View
│   │
│   ├── ProgrammeManager/
│   │   └── Dashboard.cshtml           # PM Dashboard View
│   │
│   ├── HR/
│   │   └── Dashboard.cshtml           # HR Dashboard View
│   │
│   ├── Reports/
│   │   └── ClaimReport.cshtml         # Report View (claim summary)
│   │
│   └── Shared/
│       ├── _Layout.cshtml             # Main layout template
│       └── _ValidationScriptsPartial.cshtml
│
├── Services/
│   └── FileUploadService.cs (optional) # Handles document uploads
│
├── wwwroot/
│   ├── css/
│   ├── js/
│   └── uploads/                       # Uploaded claim documents
│
├── appsettings.json
├── Program.cs
└── README.md

```

---

## 🚀 Setup Instructions

### **Prerequisites**
- Visual Studio 2026 (or VS Code with C# extension)
- .NET 9.0 SDK or later
- SQL Server (LocalDB, Express, or full version)

### **Step 1: Create Project**
```bash
# Create new ASP.NET Core MVC project
dotnet new mvc -n LecturerClaimSystem
cd LecturerClaimSystem
```

### **Step 2: Install NuGet Packages**
```bash
# dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools
dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore
dotnet add package FluentValidation.AspNetCore


```

### **Step 3: Create Database**
```bash
# Option 1: Using Package Manager Console in Visual Studio
Add-Migration InitialCreate
Update-Database

# Option 2: Using .NET CLI
dotnet ef migrations add InitialCreate
dotnet ef database update
```

### **Step 4: Run the Application**
```bash
# Using Visual Studio: Press F5
# Using CLI:
dotnet run
```

Navigate to: `https://localhost:5001`

---

## 📝 Git Commit Strategy (10 Commits)

```bash
Commit 1 – Initial project setup
Commit 2 – Identity roles + login
Commit 3 – Lecturer dashboard + claim submission
Commit 4 – PC/PM dashboards + workflow setup
Commit 5 – Approval logic + auto-approval
Commit 6 – Role-based authorization
Commit 7 – Secure uploads
Commit 8 – UI enhancements
Commit 9 – Report generation
Commit 10 – Final cleanup + documentation
```

---

## 🔐 User Roles
| Role                           | Responsibility                    |
| ------------------------------ | --------------------------------- |
| **Lecturer**                   | Submit claims, view status        |
| **Programme Coordinator (PC)** | Verify claims                     |
| **Programme Manager (PM)**     | Approve/Reject                    |
| **HR**                         | Process payment, generate reports |

---

## 🔍 Automated Business Rules

### **Validation Rules:**
- Hours: 0.01 - 300 per claim
- Rate: R0.01 - R5,000 per hour
- Period: End date must be ≥ Start date
- Documents: At least 1 required
- File types: PDF, DOCX, PNG, JPG
- File size: Max 5MB per file

### **Auto-Approval Criteria:**
- Total amount ≤ R5,000
- No validation errors
- All business rules passed
- Automatic status change to "Approved"

### **Status Workflow:**
```
Submitted → InReview → Approved/Rejected → Processed
            ↓
    (Auto-Approval if eligible)
```

---

## 📊 Testing Scenarios

### **Test Case 1: Auto-Approval**
- Hours: 20
- Rate: R200
- Total: R4,000
- **Expected**: Auto-approved

### **Test Case 2: Manual Review**
- Hours: 40
- Rate: R300
- Total: R12,000
- **Expected**: Requires manual review

### **Test Case 3: Validation Error**
- Hours: 350 (exceeds 300 max)
- **Expected**: Validation error message

### **Test Case 4: File Upload**
- Upload PDF document
- **Expected**: File uploaded successfully

---

## 🐛 Troubleshooting

### **Database Connection Issues:**
```bash
# Check SQL Server is running
# Update connection string in appsettings.json
# Verify LocalDB installation
sqllocaldb info
```

### **Migration Issues:**
```bash
# Delete existing migrations
rm -rf Migrations/
# Recreate
dotnet ef migrations add InitialCreate
dotnet ef database update
```

### **File Upload Issues:**
```bash
# Ensure wwwroot/uploads folder exists
mkdir wwwroot/uploads
# Check file permissions
```

---

## 📚 Additional Resources

- [ASP.NET Core Documentation](https://docs.microsoft.com/aspnet/core)
- [Entity Framework Core](https://docs.microsoft.com/ef/core)
- [FluentValidation](https://docs.fluentvalidation.net)
- [Bootstrap 5](https://getbootstrap.com/docs/5.0)

---

## 👨‍💻 Author

**Student**: ST10460868  
**Course**: Programming 2B  
**Framework**: ASP.NET Core MVC

---

## 📄 License

This project is for educational purposes as part of a Portfolio of Evidence (POE).

---



