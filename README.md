# DotNet API Boilerplate

## Overview

This project is a boilerplate for building .NET API applications with various features such as authentication, rate limiting, CORS, and logging using Serilog.

## Features

- [x] Authentication using JWT Bearer tokens
- [x] Rate limiting to prevent API abuse
- [x] CORS policies for secure cross-origin requests
- [x] Response caching and compression
- [x] Logging with Serilog
- [x] Health check endpoint
- [ ] Vault Integration
- [ ] MQ Integration
- [ ] Application Resiliency
- [ ] Performance Metrics
- [ ] Dockerization
- [ ] CloudFormation - Stack Deployment Template
- [ ] Github Action

## Getting Started

### Prerequisites

- [.NET 6 SDK](https://dotnet.microsoft.com/download/dotnet/6.0)
- [Keycloak](https://www.keycloak.org/) for authentication

### Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/FullstackCodingGuy/netapi-boilerplate.git
    cd netapi-boilerplate
    ```

2. Install the required NuGet packages:
    ```sh
    dotnet restore
    ```

3. Update the `appsettings.json` and `serilog.json` files with your configuration.

### Running the Application

1. Build and run the application:
    ```sh
    dotnet run
    ```

2. The application will be available at `http://localhost:5035` (or the configured URL).

### Health Check Endpoint

The application includes a health check endpoint to verify that the API is running. You can access it at:


```
GET /health

This will return a simple "Healthy" message.
```

### Logging with Serilog

Serilog is configured to log to the console and a file with daily rotation. You can customize the logging settings in the `serilog.json` file.

Example configuration in [Program.cs](http://_vscodecontentref_/1):

```csharp
Log.Logger = new LoggerConfiguration()
    .WriteTo.Console()   // Log to console
    .WriteTo.File("logs/api-log.txt", rollingInterval: RollingInterval.Day) // Log to a file (daily rotation)
    .Enrich.FromLogContext()
    .MinimumLevel.Information()
    .CreateLogger();

builder.Host.UseSerilog();
```


Additional Configuration
- Authentication: Configure the JWT Bearer options in Program.cs to match your Keycloak settings.
- CORS: Update the CORS policies in Program.cs to match your frontend URLs.
- Rate Limiting: Adjust the rate limiting settings in Program.cs as needed.
