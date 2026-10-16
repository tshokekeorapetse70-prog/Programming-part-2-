# RaceDay System

## 1. Project Overview

RaceDay is a web-based application developed using C# and ASP.NET Core Web API. The system is designed to support race event management by allowing users to register accounts, log in securely, and view available race events. It uses Microsoft SQL Server to store application data and Entity Framework Core to manage communication between the application and the database.

The system also uses JSON Web Token (JWT) authentication to verify user identities and role-based authorization to restrict access to certain functions.

## 2. Technologies Used

- **Programming Language:** C#
- **Framework:** ASP.NET Core Web API
- **Target Framework:** .NET 10
- **Database:** Microsoft SQL Server
- **Object-Relational Mapper:** Entity Framework Core
- **Authentication:** JWT Bearer Authentication
- **Password Security:** Password hashing using PasswordHasher
- **Development Environment:** Visual Studio
- **API Documentation:** OpenAPI

## 3. Main Features

- User registration with input validation.
- Secure login using email and password.
- Password hashing before storing user credentials.
- JWT token generation and validation.
- Role-based access for participants, organisers, and administrators.
- Viewing all available race events.
- Viewing individual race events.
- Creating race events for authorised organisers and administrators.
- Database relationships and constraints to help maintain data integrity.

**Note:** The current implementation provides the features listed above where their corresponding endpoints have been implemented. Event participant registration, results management, and administrative role management may require additional development.

## 4. Project Structure

- `Program.cs` — Configures application services, database access, authentication, authorization, and controller routes.
- `Models.cs` — Defines user, race event, registration, and request models.
- `RaceDayContext.cs` — Configures Entity Framework Core and the database relationships.
- `Controllers/AuthController.cs` — Handles user registration and login.
- `Controllers/EventsController.cs` — Handles retrieving and creating race events.
- `appsettings.json` — Contains the database connection and JWT configuration settings.

## 5. Prerequisites

Before running the application, ensure that you have installed:

- Visual Studio with ASP.NET and web development support.
- The .NET 10 SDK.
- Microsoft SQL Server or SQL Server LocalDB.
- The required NuGet packages for Entity Framework Core, SQL Server, and JWT authentication.

## 6. Database Configuration

The application uses SQL Server and Entity Framework Core.

1. Open `appsettings.json`.
2. Configure the `DefaultConnection` connection string to match your SQL Server instance.
3. Ensure the SQL Server service or LocalDB instance is available.
4. Confirm that the `RaceDayContext` is registered in `Program.cs`.

Example LocalDB connection string:

`Server=(localdb)\MSSQLLocalDB;Database=RaceDayDB;Trusted_Connection=True;TrustServerCertificate=True;`

## 7. JWT Configuration

The application uses JWT tokens to authenticate users.

Configure the following settings:

- `Key` — A strong, secret signing key.
- `Issuer` — The system issuing the token.
- `Audience` — The intended recipient of the token.

For security, use a development secret stored in .NET User Secrets or an environment variable. Do not commit real secrets, passwords, or production connection details to GitHub.

## 8. Installation and Setup

1. Clone or download the project repository.
2. Open the project solution in Visual Studio.
3. Restore the required NuGet packages.
4. Configure the SQL Server connection string.
5. Configure the JWT settings.
6. Open the Package Manager Console and select the correct project.
7. Create the initial database migration:

   `Add-Migration InitialCreate`

8. Apply the migration:

   `Update-Database`

9. Build the solution and resolve any compilation errors.
10. Run the application using Visual Studio.

If the initial migration already exists, use the existing migration instead of creating a duplicate.

## 9. API Endpoints

| HTTP Method | Endpoint | Description |
|---|---|---|
| POST | `/api/Auth/register` | Registers a participant account. |
| POST | `/api/Auth/login` | Authenticates a user and returns a JWT. |
| GET | `/api/Events` | Retrieves all race events. |
| GET | `/api/Events/{id}` | Retrieves a specific event. |
| POST | `/api/Events` | Creates an event for an authorised organiser or administrator. |

The event creation endpoint requires a valid JWT and an appropriate role.

## 10. Testing

The API can be tested using Swagger, when available, or an API testing tool such as Postman.

Suggested testing procedure:

1. Register a new participant account.
2. Log in using the registered email address and password.
3. Copy the JWT returned by the login endpoint.
4. Retrieve the available events.
5. Retrieve a specific event using its ID.
6. Test event creation with a valid organiser or administrator token.
7. Confirm that invalid credentials and unauthorised requests are rejected.
8. Verify that the expected records are stored in SQL Server.

## 11. Security Considerations

- Passwords are hashed rather than stored as plain text.
- JWT tokens have an expiry time.
- Protected endpoints validate the user's identity and role.
- Input validation helps reject invalid requests.
- Database constraints help prevent duplicate emails and duplicate event registrations.
- Secret keys and sensitive connection information must be stored securely.
- Production deployments should use HTTPS and appropriate logging, error handling, and security controls.

## 12. Future Improvements

Possible improvements include:

- Allowing participants to register for race events.
- Managing participant registrations and event capacity.
- Adding race results and result reporting.
- Implementing secure organiser and administrator management.
- Adding automated unit and integration tests.
- Setting up a GitHub Actions CI/CD pipeline.
- Improving error handling and API documentation.

## 13. Author and Academic Information

**Project Name:** RaceDay System  
**Student Name:** [Enter your name]  
**Student Number:** [Enter your student number]  
**Module:** [Enter your module name and code]  
**Institution:** [Enter your institution]  
**Date:** [Enter submission date]

## 14. Conclusion

The RaceDay System demonstrates the use of ASP.NET Core Web API, C#, SQL Server, Entity Framework Core, and JWT authentication in developing a race event management application. Its modular structure separates configuration, data models, database operations, and API endpoints, making the application easier to maintain and extend.
