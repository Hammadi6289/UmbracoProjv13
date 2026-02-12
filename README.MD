# Umbraco v13 Project Documentation

## Project Information

**Project Name:** XS Tech Software Solutions Website  
**Client:** XS Tech Software Solutions (Software House, Islamabad)  
**CMS:** Umbraco v13  
**Framework:** .NET 8  
**Database:** SQLite (Development)  
**Date Started:** February 2026

---

## Technology Stack

| Component                    | Version/Type                 |
| ---------------------------- | ---------------------------- |
| CMS                          | Umbraco v13.6.x              |
| .NET SDK                     | .NET 8.0                     |
| .NET Runtime                 | .NET 10.0.3 (also installed) |
| Node.js                      | v22                          |
| Database (Dev)               | SQLite                       |
| Database (Future/Production) | SQL Server (planned)         |
| IDE                          | VS Code                      |
| Terminal                     | Git Bash (MINGW64)           |

---

## Installation Steps

### 1. Prerequisites Installed

- ✅ .NET 8 SDK
- ✅ .NET 10 SDK (for other projects)
- ✅ Node.js v22
- ✅ Git Bash
- ✅ VS Code

### 2. Umbraco Template Installation

```bash
# Uninstalled the latest Umbraco templates (v17)
dotnet new uninstall Umbraco.Templates

# Installed specific Umbraco v13 templates
dotnet new install Umbraco.Templates@13.5.2

# Later upgraded to latest v13.6.x for security patches
# (See Security section below)
```

### 3. Project Creation

```bash
# Created new Umbraco project
dotnet new umbraco -n UmbracoProjv13

# Navigated to project directory
cd UmbracoProjv13

# Initial run
dotnet run
```

**Project Location:** `D:\Windows-React-app\UmbracoProjv13`

### 4. Package Installation

```bash
# Installed uSync for content synchronization
dotnet add package uSync

# Restored packages
dotnet restore
```

---

## Configuration Details

### Database Configuration

**Development Environment:**

- Using **SQLite** for local development
- Database file location: `umbraco/Data/Umbraco.sqlite.db`
- No connection string configuration needed
- Zero setup required

**Future Production/Staging:**

- Plan to migrate to **SQL Server**
- Will use environment variables for connection strings
- Migration can be done via Umbraco's built-in tools or uSync

### Application Settings

Location: `appsettings.json`

Current setup uses default SQLite configuration.

---

## Security Considerations

### Vulnerabilities Addressed

Initial installation (v13.5.2) had several moderate severity vulnerabilities:

- GHSA-4g8m-5mj5-c8xg
- GHSA-54mj-vcvj-q3v5
- GHSA-69cg-w8vm-h229
- GHSA-hfv2-pf68-m33x
- GHSA-pgvc-6h2p-q4f6

**Resolution:** Updated to Umbraco v13.6.x which includes security patches.

---

## Project Structure

```
UmbracoProjv13/
├── Properties/
│   └── launchSettings.json
├── umbraco/
│   └── Data/
│       └── Umbraco.sqlite.db (database file)
├── wwwroot/ (static files)
├── appsettings.json
├── Program.cs
├── UmbracoProjv13.csproj
└── (other Umbraco files)
```

## Development Workflow

### Running the Application

```bash
# Standard run
dotnet run

# Run with hot reload (recommended for development)
dotnet watch run

# Build only
dotnet build
```

### Accessing the Application

- **Frontend URL:** `https://localhost:44321` (or port shown in terminal)
- **Backoffice URL:** `https://localhost:44321/umbraco`
- **Default credentials:** Set during initial installation wizard

### Common Commands

```bash
# Add a NuGet package
dotnet add package PackageName

# Remove a package
dotnet remove package PackageName

# List installed packages
dotnet list package

# Restore packages
dotnet restore

# Clean build artifacts
dotnet clean
```

---

## Troubleshooting & Issues Resolved

### Issue 1: Wrong Umbraco Version Installed

**Problem:** `dotnet new install Umbraco.Templates` installed v17 instead of v13  
**Solution:** Uninstalled and specified version: `dotnet new install Umbraco.Templates::13.5.2`

### Issue 2: Missing .NET 8 Runtime

**Problem:** Project required .NET 8, but only .NET 9 and 10 were installed  
**Error:** `You must install or update .NET to run this application`  
**Solution:** Installed .NET 8 SDK from Microsoft's website

### Issue 3: Security Vulnerabilities

**Problem:** Umbraco 13.5.2 had known moderate severity vulnerabilities  
**Solution:** Updated to Umbraco 13.6.x for security patches

### Issue 4: SQL Server Connection Error

**Problem:** Attempted SQL Server connection without SQL Server installed  
**Error:** `Error: 53 - Could not open a connection to SQL Server`  
**Solution:** Switched to SQLite for development environment

### Issue 5: Wrong Package Install Command

**Problem:** Used `Install-Package` (PowerShell) in Git Bash  
**Solution:** Used `dotnet add package` instead

---

## Node.js Considerations

**Installed Version:** Node.js v22  
**Compatibility:** ✅ Umbraco 13 supports Node.js 18+  
**Usage:** Only needed for frontend build tools and backoffice customization

**Note:** No need to upgrade to Node.js v24 for Umbraco 13

---

## Database Management

### Viewing SQLite Data

**Option 1: DB Browser for SQLite**

- Download from: https://sqlitebrowser.org/
- Open: `umbraco/Data/Umbraco.sqlite.db`
- Visual interface for browsing tables

**Option 2: VS Code Extensions**

- Install: SQLite Viewer or SQLite extension
- Right-click `.db` file → "Open Database"

**Option 3: Command Line**

```bash
sqlite3 umbraco/Data/Umbraco.sqlite.db
.tables
SELECT * FROM umbracoNode;
.quit
```

### Future Migration to SQL Server

When ready to migrate to SQL Server:

1. Install SQL Server Express
2. Update `appsettings.json` with SQL Server connection string
3. Use uSync to export all content from SQLite
4. Run Umbraco with new connection string
5. Import content via uSync

---

## uSync Configuration

**Purpose:** Content synchronization and deployment between environments

**Features:**

- Export content, document types, data types, templates
- Import/restore content across environments
- Version control friendly (exports to disk as files)
- Useful for SQLite → SQL Server migration

**Usage:**

1. Access uSync in Umbraco backoffice (Settings section)
2. Export: Saves all content to disk
3. Import: Restores content from disk files

---

## Environment Setup

### Development Environment

- OS: Windows
- Terminal: Git Bash (MINGW64)
- Database: SQLite
- Debug: Visual Studio Code

### Future Production Environment (Planned)

- Database: SQL Server
- Connection strings via environment variables
- Follow employer's existing SQL Server patterns

---

## Next Steps / TODO

- [ ] Complete Umbraco initial setup wizard
- [ ] Create document types for XS Tech content
- [ ] Design page templates
- [ ] Configure uSync export/import workflow
- [ ] Plan SQL Server migration strategy
- [ ] Set up staging environment
- [ ] Configure backoffice users and permissions
- [ ] Implement custom views/components as needed

---

## Resources & Links

**Official Documentation:**

- Umbraco Docs: https://docs.umbraco.com/
- .NET 8 Docs: https://learn.microsoft.com/en-us/dotnet/
- uSync Docs: https://docs.jumoo.co.uk/usync/

**Downloads:**

- .NET 8 SDK: https://dotnet.microsoft.com/download/dotnet/8.0
- SQL Server Express: https://www.microsoft.com/sql-server/sql-server-downloads
- DB Browser for SQLite: https://sqlitebrowser.org/

**Support:**

- Umbraco Community: https://our.umbraco.com/
- Umbraco Discord: https://discord.umbraco.com/

---

## Notes

- Keep both .NET 8 and .NET 10 SDKs installed for flexibility
- SQLite is perfect for development; SQL Server for production
- uSync makes environment synchronization easy
- Regular exports recommended for backup/version control
- Security updates should be applied regularly

---

**Document Version:** 1.0  
**Maintained By:** Development Team
