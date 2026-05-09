<div align="center">

<br/>

<img src="assets/Prj_Logo.jpg" alt="TMC Logo" width="100" />

# TMC — Tauqeer Medical Center
### Clinic Management System

**A full-stack Windows desktop application built for a real-world medical clinic.**  
Handles patients, doctors, labs, billing, appointments, and administration in one unified platform.

<br/>

![Platform](https://img.shields.io/badge/Platform-Windows-0078D6?style=flat-square&logo=windows)
![Language](https://img.shields.io/badge/Language-C%23-239120?style=flat-square&logo=csharp)
![Framework](https://img.shields.io/badge/Framework-WPF%20%2F%20.NET%206-512BD4?style=flat-square&logo=dotnet)
![Database](https://img.shields.io/badge/Database-SQL%20Server-CC2927?style=flat-square&logo=microsoftsqlserver)
![IDE](https://img.shields.io/badge/IDE-Visual%20Studio%202022-5C2D91?style=flat-square&logo=visualstudio)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square)

</div>

---

## Overview

TMC is a desktop clinic management system developed specifically for **Tauqeer Medical Center**, a real operating clinic. It was built to digitize and streamline the clinic's day-to-day operations — from patient intake and doctor consultations to lab testing, invoicing, and administrative analytics.

The system supports **five distinct user roles**, each with their own dedicated portal, and follows the complete real-world patient journey through the clinic.

---

## Patient Journey (Full Cycle)

```
Patient Arrives
      │
      ▼
[Clinic Receptionist]
  Registers patient, enters details, assigns priority & doctor
      │
      ▼
[Doctor Dashboard]
  Reviews patient problem — decides:
  ├── Bed/Drip Assignment (bed number assigned, payment pending)
  ├── Lab Test Referral ──► [Lab Receptionist] runs test, shares invoice
  └── Direct Billing (routine checkup complete)
      │
      ▼
[Clinic Receptionist — Billing]
  Receives final invoice (from doctor or lab), generates bill, prints invoice
      │
      ▼
[Patient — Done]
  Receives printed invoice, payment collected
```

> Patients who return for follow-up are re-queued by the receptionist with their previous records and can be prioritized based on medical history.

---

## System Roles

| Role | Portal | Key Responsibilities |
|------|--------|---------------------|
| 🔴 **Admin** | Admin Dashboard | System-wide analytics, finance reports, age/gender stats, user management |
| 🟠 **Clinic Receptionist** | Clinic Recp Dashboard | Patient registration, queue management, billing, invoice printing |
| 🔵 **Doctor** | Doctor Portal | Patient consultation, bed assignment, lab referrals, diagnosis |
| 🟡 **Lab Receptionist** | Lab Dashboard | Test processing, result sharing, lab earnings tracking |
| ⚪ **System** | Login | Role-based authentication for all users |

---

## Screenshots

> 📁 All screenshots are in the `/Screenshots` folder.

### Login Screen
![Login](Screenshots/login.png)
*Role-based login with notice board and real-time system status panel.*

### Clinic Receptionist Dashboard
![Clinic Dashboard](Screenshots/clinic_recp_dashboard.png)
*Live stats: total patients, doctors, income, treatments. Available doctors and patient queue shown side-by-side.*

### Doctor Portal
![Doctor Dashboard](Screenshots/doctor_dashboard.png)
*Doctor accepts or rejects patients from the queue. Can assign bed numbers for drip or overnight stays.*

### Patient Waiting List (Doctor View)
![Doctor Waiting](Screenshots/doctor_waiting.png)
*Filterable patient waiting list with diagnosis, allergies, and Accept/Cancel actions.*

### Patient List
![Patient List](Screenshots/add_patient.png)
*Full patient registry: name, age, gender, appointment time, doctor, diagnosis, allergies, and status.*

### Add Patient Dialog
![Add Patient](Screenshots/add_patient_dialog.png)
*Form for registering a new patient: name, age, gender, appointment date/time, doctor, diagnosis, allergies, and problem description.*

### Doctor List
![Doctor List](Screenshots/add_doctor.png)
*Doctor registry with ID, name, age, gender, years of experience, schedule, contact, specialization, appointment fee, and availability status.*

### Billing
![Billing](Screenshots/billings.png)
*Receptionist billing view. Lists all patients with bill-action triggers for invoice generation.*

### Lab Receptionist Dashboard
![Lab Dashboard](Screenshots/lab_recp_dashboard.png)
*Lab portal: referred patients, test statuses (pending/done/cancelled), total earnings, and test counts.*

### Lab Sharables
![Lab Sharables](Screenshots/lab_sharables.png)
*Shared lab result records sent from the lab to the clinic doctor for review.*

### Invoice
![Invoice](Screenshots/invoice.png)
*Auto-generated, printable invoice with services, charges, discount, tax, and grand total.*

---

## Core Features

- **Smart Patient Queue** — Priority-based patient routing to available doctors; reassignment if doctor rejects or is unavailable
- **Role-Based Authentication** — Separate portals for Admin, Clinic Receptionist, Doctor, Lab Receptionist
- **Bed Management** — Doctors assign numbered beds for IV drips and overnight stays
- **Lab Integration** — Full cycle: doctor referral → lab test → result shared → clinic billing
- **Appointment Booking** — Phone-based appointments registered by receptionist with priority flags
- **Automated Invoicing** — Itemized invoices (consultation, lab, medication, procedures) with print support
- **Admin Analytics** — Revenue tracking, patient demographics, age/gender reports, earnings history
- **System Status Panel** — Live database connection, server status, active user count on login screen
- **Notice Board** — System-wide announcements displayed at login (maintenance, meetings, updates)

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Language | C# |
| UI Framework | WPF (Windows Presentation Foundation) / XAML |
| Runtime | .NET 6 |
| Database | Microsoft SQL Server |
| Data Access | ADO.NET |
| UI Library | MaterialDesignInXAML |
| IDE | Visual Studio 2022 |

---

## Folder Structure

```
TMC-Clinic-Management-System/
│
├── WPF_Prj/                          # Main WPF application project
│   │
│   ├── Views/                        # All XAML screens (UI)
│   │   ├── Login.xaml
│   │   ├── Admin.xaml
│   │   ├── Clinic_Recp_Dashboard.xaml
│   │   ├── Add_Doctor.xaml
│   │   ├── Add_Patient.xaml
│   │   ├── Add_Patient_Dialog.xaml
│   │   ├── Doctor_Dashboard.xaml
│   │   ├── Doctor_Waiting.xaml
│   │   ├── Doctor_Appointment.xaml
│   │   ├── Add_Patient_lab.xaml
│   │   ├── Billings.xaml
│   │   ├── DoctorSelectionDialog.xaml
│   │   ├── Lab_Recp_Dashboard.xaml
│   │   ├── Lab_Recp_Earning.xaml
│   │   ├── Lab_Receptionist_Sharables.xaml
│   │   ├── Earning.xaml
│   │   └── Invoice.xaml
│   │
│   ├── Models/                       # Data models and entities
│   ├── ViewModels/                   # Business logic (MVVM pattern)
│   ├── Helpers/                      # DB connection helpers, value converters
│   └── Resources/                    # Icons, themes, shared styles
│
├── Database/
│   └── TMC_Schema.sql                # Full SQL Server schema + seed data
│
├── Screenshots/                      # UI screenshots for README
│
└── README.md
```

---

## Getting Started

### Prerequisites

- Windows 10 / 11
- [Visual Studio 2022](https://visualstudio.microsoft.com/) with `.NET Desktop Development` workload
- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) (Express or Developer edition)
- [SQL Server Management Studio (SSMS)](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/MuhammadAnasBilal/TMC-Clinic-Management-System.git
cd TMC-Clinic-Management-System
```

**2. Set up the database**

Open SSMS and run the file:
```
Database/TMC_Schema.sql
```

**3. Update the connection string**

In `WPF_Prj/Helpers/DBHelper.cs`, update the connection string with your SQL Server instance name:
```csharp
string connectionString = "Server=YOUR_SERVER_NAME;Database=TMC_DB;Integrated Security=True;";
```

**4. Install NuGet packages**

Open the solution in Visual Studio. NuGet packages (including MaterialDesignInXAML) should restore automatically. If not:
```
Tools → NuGet Package Manager → Manage NuGet Packages for Solution → Restore
```

**5. Run**

Press `F5` or click ▶ **Start** in Visual Studio.

Default login credentials are seeded in the database (see `Database/TMC_Schema.sql`).

---

## Database Schema (Overview)

| Table | Description |
|-------|-------------|
| `Users` | System users with roles (Admin, Doctor, Receptionist, LabRecp) |
| `Patients` | Patient records with medical and appointment details |
| `Doctors` | Doctor profiles, schedules, specializations, fees |
| `Queue` | Patient queue with priority and assignment info |
| `Beds` | Bed availability and assignments |
| `LabTests` | Lab test orders, statuses, and results |
| `Billing` | Invoice records with itemized charges |
| `Appointments` | Appointment bookings (phone/walk-in) |
| `Notices` | System-wide notice board announcements |

---

## Team

| Name | Role |
|------|------|
| **Muhammad Anas Bilal** | Lead Developer — UI/UX, Backend, Database |

> *Built as a real-world DB course project, deployed for Tauqeer Medical Center.*

---

## License

This project was developed for **Tauqeer Medical Center** as part of a university DB project. It is shared for educational and portfolio purposes.

---

<div align="center">
<br/>
Made with ❤️ for Tauqeer Medical Center · 2025
</div>
