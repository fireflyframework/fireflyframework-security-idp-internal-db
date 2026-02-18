# Firefly Framework - IDP - Internal Database

[![CI](https://github.com/fireflyframework/fireflyframework-idp-internal-db/actions/workflows/ci.yml/badge.svg)](https://github.com/fireflyframework/fireflyframework-idp-internal-db/actions/workflows/ci.yml)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Java](https://img.shields.io/badge/Java-21%2B-orange.svg)](https://openjdk.org)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-green.svg)](https://spring.io/projects/spring-boot)

> Internal database-based IDP implementation using R2DBC for user management, JWT authentication, and role-based access control.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Configuration](#configuration)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)

## Overview

Firefly Framework IDP Internal Database implements the `IdpAdapter` interface using a local database as the identity store. It provides complete user management, authentication, JWT token generation and validation, session tracking, and role-based access control using R2DBC for reactive database access.

The module includes domain entities for users, roles, sessions, and refresh tokens, with corresponding R2DBC repositories. The `AuthenticationService` handles login/logout flows, `JwtTokenService` manages JWT creation and validation, and `UserManagementService` provides CRUD operations for user administration.

This implementation is suitable for applications that need self-contained identity management without external IDP dependencies.

## Features

- Full `IdpAdapter` implementation with internal database storage
- R2DBC-based reactive repositories for users, roles, sessions, and tokens
- JWT token generation and validation via `JwtTokenService`
- Authentication service with login, logout, and token refresh
- Role-based access control with user-role assignments
- Refresh token management with rotation support
- Session tracking and management
- User management service for CRUD operations
- Configurable via `InternalDbProperties`

## Requirements

- Java 21+
- Spring Boot 3.x
- Maven 3.9+
- PostgreSQL database (for user store)

## Installation

```xml
<dependency>
    <groupId>org.fireflyframework</groupId>
    <artifactId>fireflyframework-idp-internal-db</artifactId>
    <version>26.02.05</version>
</dependency>
```

## Quick Start

```xml
<dependencies>
    <dependency>
        <groupId>org.fireflyframework</groupId>
        <artifactId>fireflyframework-idp</artifactId>
    </dependency>
    <dependency>
        <groupId>org.fireflyframework</groupId>
        <artifactId>fireflyframework-idp-internal-db</artifactId>
    </dependency>
</dependencies>
```

## Configuration

```yaml
firefly:
  idp:
    internal-db:
      jwt:
        secret: your-jwt-secret-key
        expiration: 3600
        refresh-expiration: 86400
spring:
  r2dbc:
    url: r2dbc:postgresql://localhost:5432/idp
```

## Documentation

Additional documentation is available in the [docs/](docs/) directory:

- [Readme](docs/README.md)
- [Api](docs/API.md)
- [Dto Field Mapping](docs/DTO_FIELD_MAPPING.md)
- [Integration](docs/INTEGRATION.md)
- [Project Status](docs/PROJECT_STATUS.md)
- [Technical Details](docs/technical-details.md)

## Contributing

Contributions are welcome. Please read the [CONTRIBUTING.md](CONTRIBUTING.md) guide for details on our code of conduct, development process, and how to submit pull requests.

## License

Copyright 2024-2026 Firefly Software Solutions Inc.

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.
