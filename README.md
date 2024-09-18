
# MASAR Transportation Management System
MASAR is a transportation management system designed to manage buses, drivers, students, maintenance requests, schedules, and more. This system is built with ASP.NET Core for the backend, Entity Framework Core for database interaction, and implements JWT authentication for user authorization.

## Table of Contents
- Installation
- Technologies Used
- Project Structure
- API Endpoints
  - Users
  - Buses
  - Drivers
  - Students
  - Announcements
- Database Models
- License

## Installation
Clone the repository to your local machine:

```bash
git clone https://github.com/your-repository-url.git
```

Navigate to the project directory:

```bash
cd MASAR-Transportation-System
```

Install the required dependencies:

```bash
dotnet restore
```

Set up the database by updating the connection string in `appsettings.json` and running the migrations:

```bash
dotnet ef database update
```

Run the application:

```bash
dotnet run
```

## Technologies Used
- ASP.NET Core
- Entity Framework Core
- JWT Authentication
- SQL Server
- Microsoft Identity
- C#

## Project Structure
The project is divided into several folders, each serving different responsibilities:

### Controllers:
Contains the API controllers that manage requests and responses.

- **AdminController.cs**: Handles admin-specific functionality like creating announcements and approving maintenance requests.
- **UsersController.cs**: Manages user login, logout, and updates.
- **BusesController.cs**: Manages bus creation and location tracking.
- **DriverController.cs**: Manages driver profiles and maintenance requests.
- **StudentController.cs**: Handles student registration and announcements.

### Models:
Defines the structure of the data objects used within the system.

- **ApplicationUser.cs**: User entity that extends Microsoft Identity's IdentityUser.
- **Bus.cs**: Represents a bus in the system, including plate number and status.
- **DriverProfile.cs**: Stores driver details and related bus.
- **Schedule.cs**: Manages bus schedules and routing.
- **Maintenance.cs**: Handles maintenance requests for buses.

### Data:
Handles the interaction between the application and the database using Entity Framework Core.

- **MASARDBContext.cs**: The database context class managing all entity relationships and seeding data.

### Services:
Business logic and service layer for the application.

- **BusService.cs**: Implements the business logic for managing bus data.

### Repositories:
Contains interfaces defining repository patterns.

- **IBus.cs**: Interface for bus-related operations.
- **IDriver.cs**: Interface for driver-related operations.
- **IStudent.cs**: Interface for student-related operations.
- **IUser.cs**: Interface for user-related operations.

## API Endpoints

### Users
- `POST /api/Users/Login`: Login a user.
- `POST /api/Users/Logout`: Logout a user.
- `GET /api/Users/ViewAllAnnouncement`: View all announcements available to the user.

### Buses
- `POST /api/Buses/CreateBusByAdmin`: Create a bus (admin only).
- `POST /api/Buses/updateBusLocation`: Update the bus's location.
- `GET /api/Buses/getBusLocation`: Get the location of a specific bus.

### Drivers
- `POST /api/Driver/CreateDriverInfo`: Create driver info.
- `POST /api/Driver/MaintenanceRequest`: Submit a maintenance request for a bus.

### Students
- `POST /api/Student/StudentRigester`: Register a new student.
- `GET /api/Student/ViewAllAnnouncement`: View all announcements for students.

### Announcements
- `POST /api/Admin/CreateAnnouncementByAdmin`: Create an announcement (admin only).

## Database Models

- **ApplicationUser**: Represents a user in the system, including their roles (Admin, Student, Driver).
- **Bus**: Represents the details of a bus such as plate number, capacity, and current location.
- **DriverProfile**: Stores details about drivers and their assigned buses.
- **Schedule**: Manages the schedule of buses, linked to routing information.
- **Announcement**: Stores announcements created by admins, targeted to users.

## License
This project is licensed under the MIT License. See the LICENSE file for details.
