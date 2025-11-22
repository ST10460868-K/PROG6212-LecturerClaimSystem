# 📚 Lecturer Monthly Claim System
## ASP.NET Core MVC - Automated Verification & Approval System

### 🎯 Project Overview

The Lecturer Monthly Claim System is a full-stack ASP.NET Core MVC web application that automates the submission, validation, approval, and processing of monthly lecturer claims.

The system ensures accuracy through auto-calculation, strict business rule validation, automated approval (for claims under R5,000), and a professional, user-friendly interface. It supports both lecturer submissions and coordinator/manager workflows.
---

## ✨ Key Features

### ✅ **Automated Verification & Approval **
- Real-time auto-calculation of claim totals
- Automated validation with business rules
- Auto-approval for claims under R5,000 threshold
- Comprehensive error checking and validation

### ✅ **Claim Processing Automation **
- Automated status tracking (Submitted → InReview → Approved/Rejected → Processed)
- Structured data management with Entity Framework Core
- Bulk approval functionality
- Streamlined administrative workflows

### ✅ **Professional GUI Design **
- Modern Bootstrap 5 interface
- Responsive design for all devices
- Intuitive navigation with clear visual hierarchy
- Professional color scheme and layout

### ✅ **User-Friendly Interface **
- Clear form labels with icons
- Inline validation feedback
- File upload with preview
- Real-time calculation display

### ✅ **Auto-Calculation Feature **
- jQuery-based client-side calculation
- Server-side validation redundancy
- Instant total updates as user types
- Auto-approval eligibility indicator

### ✅ **Version Control Ready **
- Structured for meaningful commits
- Clear separation of concerns
- Modular architecture

---

## 🛠️ Technology Stack

- **Framework**: ASP.NET Core 9.0 MVC
- **Database**: Entity Framework Core with SQL Server
- **Validation**: FluentValidation
- **Frontend**: Bootstrap 5, jQuery, Font Awesome
- **Testing**: xUnit (optional)

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
# Entity Framework Core
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools

# FluentValidation
dotnet add package FluentValidation.AspNetCore

# Optional: For testing
dotnet add package xunit
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### **Step 3: Add All Code Files**
Copy all the provided code files into the appropriate folders:
- `Models/CompleteModels.cs`
- `Data/AppDbContext.cs`
- `Services/FileUploadService.cs`
- `Validators/ClaimValidator.cs`
- `Controllers/LecturerController.cs`
- `Controllers/CoordinatorController.cs`
- `Views/Lecturer/Create.cshtml`
- `Program.cs`
- `appsettings.json`

### **Step 4: Update Connection String** (Optional)
Edit `appsettings.json` if needed:
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=LecturerClaimSystemDB;Trusted_Connection=true"
  }
}
```

### **Step 5: Create Database**
```bash
# Option 1: Using Package Manager Console in Visual Studio
Add-Migration InitialCreate
Update-Database

# Option 2: Using .NET CLI
dotnet ef migrations add InitialCreate
dotnet ef database update
```

### **Step 6: Run the Application**
```bash
# Using Visual Studio: Press F5
# Using CLI:
dotnet run
```

Navigate to: `https://localhost:5001`

---

## 📝 Git Commit Strategy (10 Commits)

```bash
commit 1
Initial project setup with ASP.NET Core MVC, Entity Framework Core, and SQL Server database
- Added models (Claim, ApplicationUser, ClaimStatistics)
- Configured DbContext and connection string
- Implemented basic folder structure and Program.cs

commit 2
Implemented full Identity authentication with roles (Lecturer, Coordinator, Admin)
- Added ApplicationUser inheriting from IdentityUser
- Seeded test users and roles on startup
- Added login/logout functionality with proper redirects

commit 3
Developed fully functional Lecturer dashboard and claim submission
- Created LecturerController with Index, Create actions
- Built responsive Lecturer/Index.cshtml with beautiful table, badges, and styling
- Implemented claim submission with automatic TotalAmount calculation and Submitted status

commit 4
Built stunning Coordinator/Manager dashboard with real-time statistics
- Designed modern UI with cards, gradient header, hover effects
- Implemented statistics (Total Claims, Submitted, Approved, Total Amount, etc.)
- Added Bulk Auto-Approve button with confirmation

commit 5
Implemented complete claim review and approval workflow
- Created Review, Approve, Reject, Details, and Pending actions
- Added automated validation checks and auto-approval under R5,000 threshold
- Integrated reviewer comments and status transitions

commit 6
Added role-based authorization and secured all controllers
- Applied [Authorize(Roles = "Lecturer")] and [Authorize(Roles = "Coordinator,Admin")]
- Ensured lecturers can only see their claims
- Protected coordinator actions from unauthorized access

commit 7
Enhanced UI/UX with professional styling and user feedback
- Added success/error TempData messages with alerts
- Implemented FontAwesome icons throughout
- Added hover effects, shadows, badges, and responsive design
- Created clean "No claims" states with icons

commit 8
Final polish, bug fixes, and production-ready improvements
- Fixed routing and Identity Razor pages integration
- Improved date formatting and currency display (R0.00)
- Added anti-forgery tokens and input validation
- Cleaned code, added comments, and ensured 100% functionality
```

---

## 🎮 Usage Guide

### **For Lecturers:**
1. Navigate to `/Lecturer/Create`
2. Fill in the claim form:
   - Select period dates
   - Enter hours worked
   - Enter hourly rate
   - Watch total auto-calculate
3. Upload supporting documents (PDF, DOCX, images)
4. Submit claim
5. View status on `/Lecturer/MyClaims`

### **For Coordinators:**
1. Navigate to `/Coordinator/Index` (dashboard)
2. View all claims with statistics
3. Click "Review" on any claim
4. System performs automated checks:
   - If eligible (≤ R5,000): Auto-approved
   - If not eligible: Manual review required
5. Approve/Reject with comments
6. Use "Bulk Auto-Approve" for batch processing

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



