# SonarQube configuration settings

This describes the configuration settings for SonarQube

## Analysis Scope

### Source File Exclusions

Exclude external code that is added to work around limitations of that code:

```
**/ol/**/*.java
**/com/**/*.java
**/com/**/*.js
```

### Ignore Issues on Multiple Criteria

Ignore reporting on the following rules because limitations of the framework, like restrictions on classes for client/server communication, we can't enforce these rules on the specific code.

| Rule Key Pattern                         | File Path Pattern                           |
|------------------------------------------|---------------------------------------------|
| `java:S1612`                             | `**/aerius-calculator-wui-client/**/*.java` |
| `java:S2039`                             | `**/aerius-calculator-wui-client/**/*.java` |
| `java:S3052`                             | `**/aerius-calculator-wui-client/**/*.java` |
| `common-java:InsufficientLineCoverage`   | `**/aerius-calculator-wui-client/**/*.java` |
| `common-java:InsufficientBranchCoverage` | `**/aerius-calculator-wui-client/**/*.java` |
