# Spring PetClinic Sample Application

This project is a fork of original Spring PetClinic application modified to
trigger inspections provided by IJ IDEA Ultimate.

## List of Inspections

| #   | Subsystem   | Inspection                                     | Highlighted for                                  |
|-----|-------------|------------------------------------------------|--------------------------------------------------|
| 1   | Spring Data | SpringDataRepositoryMethodParametersInspection | `PetRepository#findByType`                       |
| 2   |             | SpringDataMethodInconsistencyInspection        | `OwnerRepository#findByName`                     |
| 3   |             | SpringDataRepositoryMethodReturnTypeInspection | `PetRepository#findByName`                       |
| 4   | Spring Boot | SpringBootApplicationPropertiesInspection      | `application.properties`                         |
| 5   |             | SpringBootApplicationSetupInspection           | `PetClinicApplication`                           |
| 6   |             | ConfigurationPropertiesInspection              | `GeneralConfig`                                  |
| 7   | Spring Core | SpringAutowiringInspection                     | `OwnerController` constructors                   |
| 8   |             | SpringJavaStaticMembersAutowiringInspection    | `PetController#generalConfig`                    |
| 9   |             | SpringJavaAutowiredFieldsWarningInspection     | `PetController#generalConfig`                    |
| 10  |             | SpringDependsOnUnresolvedBeanInspection        | `EntityRequestedEventPublisher`                  |
| 11  |             | ContextJavaBeanUnresolvedMethodsInspection     | `PetFormatterProvider#petFormatter`              |
| 12  |             | SpringCacheNamesInspection                     | `OwnerController#findAllOwners`                  |
| 13  |             | SpringEventListenerInspection                  | `EntityRequestedEventListener#onEntityRequested` |
| 14  |             | SpringComponentScanInspection                  | `PetClinicApplication`                           |
| 15  | Spring MVC  | SpringMVCViewInspection                        | `PetController#getAllPets`                       |
| 16  |             | MVCPathVariableInspection                      | `PetController#getAllPets`                       |
| 17  |             | SpringMVCInitBinderInspection                  | `OwnerController#setAllowedFields`               |

## Inspection Descriptions

### Spring Data

#### 1. Spring Data Repository Method Parameters Inspection

Reports Spring Data CRUD repository method parameters with incorrect types:

![SpringDataRepositoryMethodParametersInspection](./etc/SpringDataRepositoryMethodParametersInspection.png)

#### 2. Spring Data Method Inconsistency Inspection

Reports Spring Data CRUD repository methods for which the Spring Data Query
builder cannot generate the corresponding query.

![SpringDataMethodInconsistencyInspection](./etc/SpringDataMethodInconsistencyInspection.png)

#### 3. Spring Data Repository Method Return Type Inspection

Reports Spring Data CRUD repository methods with incorrect return types:

![SpringDataRepositoryMethodReturnTypeInspection](./etc/SpringDataRepositoryMethodReturnTypeInspection.png)

### Spring Boot

#### Spring Boot Application Properties Inspection

Reports unresolved and deprecated configuration keys and invalid values in
Spring Boot application `.properties` configuration files, which can lead
to runtime errors:

![SpringBootApplicationPropertiesInspection.logging-file](./etc/SpringBootApplicationPropertiesInspection.logging-file.png)

![props.poll-interval](./etc/SpringBootApplicationPropertiesInspection.poll-interval.png)

#### Spring Boot Application Setup Inspection

Reports `@SpringBootApplication` in the default package and redundant
`@EnableAutoConfiguration` or `@ComponentScan` annotations.
The quick-fix removes the redundant annotations:

![SpringBootApplicationSetupInspection](./etc/SpringBootApplicationSetupInspection.png)

#### Configuration Properties Inspection

Reports invalid prefixes defined in the `@ConfigurationProperties` annotations:

* Missing prefix
* Empty prefix
* Duplicate prefix
* Prefix in notation other than kebab-case

![ConfigurationPropertiesInspection](./etc/ConfigurationPropertiesInspection.png)

### Spring

#### Spring Autowiring Inspection

Reports autowiring problems on injection points of Spring beans:
 
* More than one bean of 'concrete' type
* No beans of 'concrete' type
* No bean with qualifier
* Incorrect usages of `@Autowired` on Spring bean constructors
* Injected or autowired fields/methods in classes that are not valid Spring beans

![SpringAutowiringInspection](./etc/SpringAutowiringInspection.png)

#### Spring Java Static Members Autowiring Inspection

Reports autowired and injected static methods/fields of Spring components:

![SpringJavaStaticMembersAutowiringInspection](./etc/SpringJavaStaticMembersAutowiringInspection.png)

#### Spring Java Autowired Fields Warning Inspection

Reports injected or autowired fields in Spring components.

The quick-fix suggests the recommended constructor-based dependency injection
in beans and assertions for mandatory fields.

![SpringJavaAutowiredFieldsWarningInspection](./etc/SpringJavaAutowiredFieldsWarningInspection.png)

#### Spring Depends on Unresolved Bean Inspection

Reports incorrect bean references in the value parameter of the `@DependsOn` annotation:

![SpringDependsOnUnresolvedBeanInspection](./etc/SpringDependsOnUnresolvedBeanInspection.png)


#### Context Java Bean Unresolved Methods Inspection

Reports unresolved method references on `initMethod` and `destroyMethod` parameters `@Bean` annotation:

![ContextJavaBeanUnresolvedMethodsInspection](./etc/ContextJavaBeanUnresolvedMethodsInspection.png)

#### Spring Cache Names Inspection

Reports incorrect `@Cache*` annotation names.

At least one cache name should be provided per cache operation:
`@Cacheable("cache_name")` or `@Cacheable(cacheNames ="cache_name")`.

`@CacheConfig#cacheNames()` can be used for sharing common cache-related settings at the class level.

![SpringCacheNamesInspection](./etc/SpringCacheNamesInspection.png)

#### Spring Event Listener Inspection

Reports incorrect `@EventListener` methods:

![SpringEventListenerInspection](./etc/SpringEventListenerInspection.png)

#### Spring Component Scan Inspection

![SpringComponentScanInspection](./etc/SpringComponentScanInspection.png)

### Spring MVC

#### Spring MVC View Inspection

Reports unresolved Spring MVC View references:

![SpringMVCViewInspection](./etc/SpringMVCViewInspection.png)

#### MVC Path Variable Inspection

Reports `@PathVariable` parameters that are declared in the method signature
but are absent in the URL path or vice versa. The quick-fix adds the missing parameter:

![MVCPathVariableInspection](./etc/MVCPathVariableInspection.png)

#### Spring MVC Init Binder Inspection

Reports Spring MVC Controller methods annotated with `@InitBinder` that are not declared as void:

![SpringMVCInitBinderInspection](./etc/SpringMVCInitBinderInspection.png)
