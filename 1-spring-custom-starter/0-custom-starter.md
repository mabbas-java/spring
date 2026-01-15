#### Spring custom starter notable points

> This file (
spring-configuration-metadata.json
) is a Spring Boot configuration metadata descriptor that enables IDE support for your custom configuration properties.

##### It provides:
1. IDE autocomplete in application.properties or application.yml
2. Documentation hints when hovering over properties
3. Type validation for property values
4. Default value information

> When developers use your Spring Boot starter, they can configure these properties in application.yml

### spring.factories (Spring Boot 1.x & 2.x)

#### Auto-Configuration for Spring Boot 2.x
```html
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
ae.emaratech.vip.starter.core.autoconfigure.VipCoreAutoConfiguratio

```

**Purpose**: Legacy mechanism for auto-configuration
**Format**: Properties file with key-value pairs
###### How it works:

* Spring Boot scans all
* spring.factories
* files on the classpath
* Looks for the key org.springframework.boot.autoconfigure.EnableAutoConfiguration
* Loads the specified configuration class (VipCoreAutoConfiguration)
* The backslash (\) is a line continuation character
* Used in: Spring Boot 1.x and 2x

### AutoConfiguration.imports  (Spring Boot 3.x)

> org.springframework.boot.autoconfigure.AutoConfiguration.imports:1-2

```html
ae.emaratech.vip.starter.core.autoconfigure.VipCoreAutoConfiguration

```

**Purpose**: Modern mechanism for auto-configuration
**Format**: Simple text file with one fully-qualified class name per line
**Location**:META-INF/spring/ directory

#### How it works:
* Spring Boot 3.x scans for
* org.springframework.boot.autoconfigure.AutoConfiguration.imports
* files
* Each line specifies an auto-configuration class to load
* Simpler format - no key-value pairs, just class names
* Used in: Spring Boot 3.x and later

> Always add both in starter it will  maintains backward compatibility:

* Projects using Spring Boot 2.x will use spring.factories
* Projects using Spring Boot 3.x will use AutoConfiguration.imports
* This allows your starter library to work across multiple Spring Boot versions.