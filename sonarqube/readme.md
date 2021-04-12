# SonarQube configuration settings

This describes the configuration settings for SonarQube

## Analysis Scope

### Duplication Exclusions

Exclude GML versions as these need to be duplicated to support different GML versions
```
src/main/java/nl/overheid/aerius/gml/v*/**
```

Exclude generated code for the connect api
```
src/main/java/nl/overheid/aerius/connect/domain/**
```

### Source File Exclusions

Exclude external code that is added to work around limitations of that code:

```
**/org/gwtopenmaps/openlayers/**
**/com/google/**
target/**
**/ol/style/**
**/ol/source/**
```

### Ignore Issues on Multiple Criteria

Ignore reporting on the following rules because limitations of the framework, like restrictions on classes for client/server communication, we can't enforce these rules on the specific code.

| Rule Key Pattern     | File Path Pattern                                |
|----------------------|--------------------------------------------------|
| `pmd:ImmutableField` | `src/main/java/nl/overheid/aerius/shared/**`     |
| `pmd:ImmutableField` | `src/main/java/nl/overheid/aerius/geo/shared/**` |
| `squid:S1165`        | `src/main/java/nl/overheid/aerius/shared/**`     |
| `squid:S1165`        | `src/main/java/nl/overheid/aerius/geo/shared/**` |
| `squid:S1185`        | `src/main/java/nl/overheid/aerius/gml/**`        |
| `squid:S1641`        | `src/main/java/nl/overheid/aerius/shared/**`     |
| `squid:S2245`        | `src/main/java/nl/overheid/aerius/wui/**`        |


## Languages

### Java

#### Checker Filters

```
<module name="SuppressionFilter">
    <property name="file" value="https://raw.githubusercontent.com/aerius/tools/main/sonarqube/checkstyle-suppressions.xml"/>
</module>
```

#### Treewalker Filters

```
<module name="SuppressionCommentFilter" />
```