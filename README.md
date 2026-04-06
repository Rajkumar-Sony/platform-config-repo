# Platform Config Repository

[![License](https://img.shields.io/badge/License-All%20Rights%20Reserved-red)](#license)

Centralized Spring Cloud Config repository for storing environment-specific configuration files shared across platform services.

## Purpose

- Single source of truth for service configuration across all environments
- Keep service code repositories free from runtime secrets
- Enable cross-project reuse by mapping as a Git submodule
- Support encrypted secrets with `{cipher}` prefix

## Structure

| File | Description |
|------|-------------|
| `application.yml` | Shared defaults (Eureka, Kafka, Zipkin endpoints) |
| `application-dev.yml` | Development profile overrides (DEBUG logging, test credentials) |
| `auth-service.yml` | Auth service-specific config (PostgreSQL, Keycloak, Flyway) |

Additional service configs follow the pattern `<service-name>.yml`.

## Usage

Add as a submodule in your root project:

```bash
git submodule add https://github.com/Rajkumar-Sony/platform-config-repo.git config-repo
git submodule update --init --recursive
```

Config Server references this repository:

```yaml
spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/Rajkumar-Sony/platform-config-repo
```

## Part Of

This repository is a submodule of [Cloud Drive Microservice](https://github.com/Rajkumar-Sony/Drive-Microservices).

## License

Copyright (c) 2026 Rajkumar Sony. All rights reserved. See [LICENSE](LICENSE) for details.
