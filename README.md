# platform-config-repo

Centralized Spring Cloud Config repository shared by multiple root projects.

## Purpose

- Store environment-specific configuration files for services.
- Keep service code repositories free from runtime environment secrets.
- Enable cross-project reuse by mapping this repository as a submodule.

## AI Code Generation Prerequisite (`code-review-graph`)

Install first if missing:

```bash
if ! command -v code-review-graph >/dev/null 2>&1; then
  /usr/local/bin/python3.12 -m pip install --user code-review-graph
  export PATH="$HOME/Library/Python/3.12/bin:$PATH"
fi
```

Use during AI generation/review:

```bash
code-review-graph update
code-review-graph detect-changes
```

## Structure

- `application.yml`: shared defaults
- `application-dev.yml`: development overrides
- `<service-name>.yml`: service-specific configuration

## Usage

In a root project:

```bash
git submodule add https://github.com/Rajkumar-Sony/platform-config-repo.git config-repo
git submodule update --init --recursive
```

Config Server example:

```yaml
spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/Rajkumar-Sony/platform-config-repo
```
