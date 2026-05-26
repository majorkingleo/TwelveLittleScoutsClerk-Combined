# TwelveLittleScoutsClerk-Combined

## Project page can be found there

[TwelveLittleScoutsClerk)[https://github.com/majorkingleo/TwelveLittleScoutsClerk]

## This parent project is for debugging and testing purposes

Combined Maven multi-module workspace for integrated development of two repositories:

| Module | Artifact | Description |
|---|---|---|
| `FrameWork/` | `at.redeye:framework` | Reusable Swing application framework (DB abstraction, UI base classes, i18n, user management) |
| `TwelveLittleScoutsClerk/` | `at.redeye:twelvelittlescoutsclerk` | Scout membership and financial management application |

The aggregator POM at the root builds FrameWork first, then TwelveLittleScoutsClerk, so both can be developed and debugged together without installing FrameWork to the local Maven repository between changes.

## What the application does

TwelveLittleScoutsClerk helps scout groups manage members, events, and finances — from tracking registrations through generating PDF/ODT invoices to dispatching those invoices by email. See [TwelveLittleScoutsClerk/README.md](TwelveLittleScoutsClerk/README.md) for a full feature description.

## Requirements

- Java 21
- Maven 3

## Building

All commands are run from this combined root.

```bash
# Compile both modules
mvn clean compile

# Build executable JAR (skips tests)
mvn package -DskipTests

# Run tests
mvn clean test

# Install both modules to the local Maven repository
mvn clean install -DskipTests
```

The packaged application JAR lands in `TwelveLittleScoutsClerk/target/`.

## Running

```bash
java -jar TwelveLittleScoutsClerk/target/TwelveLittleScoutsClerk-*.jar
```

## Project structure

```
pom.xml                        ← aggregator POM (builds both modules in order)
FrameWork/                     ← framework module
  src/at/redeye/
    FrameWork/                 ← core dialogs, base classes, widgets, reports
    SqlDBInterface/            ← SQL abstraction and DB connectivity
    UserManagement/            ← user and permission management
    Communication/             ← network abstractions
    Setup/                     ← configuration, export, setup wizard
TwelveLittleScoutsClerk/       ← application module
  src/at/redeye/
    twelvelittlescoutsclerk/   ← application source
```

## License

See the LICENSE file in each submodule.
