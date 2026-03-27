# cloud-drive-config

Centralized Spring Cloud Config repository shared by multiple root projects.

## Purpose

- Store environment-specific configuration files for services.
- Keep service code repositories free from runtime environment secrets.
- Enable cross-project reuse by mapping this repository as a submodule.

## Structure

- `application.yml`: shared defaults
- `application-dev.yml`: development overrides
- `<service-name>.yml`: service-specific configuration

## Usage

In a root project:

```bash
git submodule add https://github.com/Rajkumar-Sony/cloud-drive-config.git cloud-drive-config
git submodule update --init --recursive
```

Config Server example:

```yaml
spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/Rajkumar-Sony/cloud-drive-config
```
