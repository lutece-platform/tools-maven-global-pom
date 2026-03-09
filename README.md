# Lutece Global POM

Parent POM for all [Lutece](https://lutece.paris.fr) platform Maven projects.

## Overview

This POM centralizes build configuration, plugin versions, dependency versions, and quality analysis settings so that all Lutece 7.x modules inherit a consistent build.

## Requirements

| Requirement | Minimum Version |
|-------------|-----------------|
| Java        | 11              |
| Maven       | 3.3.9           |

## Key Features

### Dependencies

Inherited dependencies for all child modules:

| Dependency | Version | Scope |
|------------|---------|-------|
| Jakarta Servlet API | 4.0.4 | provided |
| Jakarta JSP API | 2.3.6 | provided |
| library-lutece-unit-testing | 4.1.1 | test |
| build-config | 2.0.3 | provided |

### Build Plugins

The POM configures the following plugins for all child modules:

| Plugin | Purpose |
|--------|---------|
| `maven-compiler-plugin` | Compilation (Java 11 release) |
| `maven-surefire-plugin` | Unit test execution with JaCoCo agent |
| `jacoco-maven-plugin` | Code coverage |
| `maven-war-plugin` | WAR packaging (source: `webapp/`) |
| `maven-checkstyle-plugin` | Code style checks (Lutece rules) |
| `maven-pmd-plugin` | Static analysis (Lutece rules) |
| `spotbugs-maven-plugin` | Bug detection (includes FindSecBugs) |
| `formatter-maven-plugin` | Code formatting (Lutece formatter) |
| `license-maven-plugin` | License header checks |
| `maven-release-plugin` | Release management (JGit SCM provider) |
| `lutece-maven-plugin` | Lutece-specific build lifecycle |
| `xdoc2md-maven-plugin` | xdoc to Markdown conversion |
| `maven-antrun-plugin` | SQL init scripts and DB property replacement |
| `maven-javadoc-plugin` | Javadoc generation |
| `maven-site-plugin` | Site generation (en/fr) |

### Reporting

Site reports (`mvn site`) include: JXR cross-reference, project info, Checkstyle, PMD, JDepend, tag list (TODO/FIXME), SpotBugs, Surefire test reports, JaCoCo coverage, Sonar link, and the Lutece report plugin.


### Project Structure Conventions

This POM expects the following source layout in child modules:

```
src/java/    # Main Java sources (instead of src/main/java)
src/test/    # Test sources and resources
webapp/      # WAR source directory (instead of src/main/webapp)
```

## Usage

Add this POM as the parent in your Lutece module:

```xml
<parent>
    <groupId>fr.paris.lutece.tools</groupId>
    <artifactId>lutece-global-pom</artifactId>
    <version>7.X.Y</version>
</parent>
```

## Repositories

- **Releases:** `https://dev.lutece.paris.fr/maven_repository`
- **Snapshots:** `https://dev.lutece.paris.fr/snapshot_repository`

## License

[Lutece License](https://dev.lutece.paris.fr/LICENSE.TXT)

## Links

- **Website:** https://lutece.paris.fr
- **Source:** https://github.com/lutece-platform/tools-maven-global-pom
- **CI:** https://dev.lutece.paris.fr/jenkins/
- **Issue Tracker:** https://dev.lutece.paris.fr/jira/browse/GLOBALPOM
