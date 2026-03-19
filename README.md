# Java Learning Project: Annotations, Generics & Lambdas

A hands-on educational project covering three core Java topics with practical examples built around a car database domain model.

## Topics Covered

### Annotations (`com.annotation`)
Custom annotations with runtime reflection processing:
- `@AnimalRequired` — class-level annotation
- `@FieldRequired` — field-level annotation
- `@RunInmmediately(times)` — method-level annotation with parameters

The `AnnotationApplication` uses reflection to discover and invoke annotated classes, fields, and methods at runtime.

### Generics (`com.generic`)
Type-safe collections and bounded wildcard patterns:
- Inheritance hierarchy: `Being` → `Animal`, `Snake`
- Bounded wildcards: `List<? extends Being>`
- Generic method demonstrations

### Lambdas (`com.lambda`)

| Sub-module | Description |
|---|---|
| `lambdas` | Custom `@FunctionalInterface`, anonymous class → lambda migration, method references (static, constructor, object, arbitrary), built-in interfaces (`Function`, `BiFunction`, `Predicate`, `Consumer`, `Supplier`, `UnaryOperator`, `BinaryOperator`) |
| `streams` | Intermediate operators (`filter`, `map`, `flatMap`, `distinct`, `limit`, `skip`, `sorted`, `takeWhile`, `dropWhile`, `peek`), terminal operators (`count`, `match`, `find`, `reduce`, `max`, `min`), collectors with grouping and partitioning |
| `optional` | `Optional.of`, `ofNullable`, `map`, `flatMap`, `orElse` |
| `concurrency` | Parallel streams with performance benchmarking |
| `real` | File I/O with streams, Strategy pattern, Comparators, generic `Validator<T, E>` framework |

## Project Structure

```
src/
└── com/
    ├── annotation/          # Custom annotations + reflection
    │   ├── interfaces/
    │   └── impl/
    ├── generic/             # Generics + wildcards
    │   ├── model/
    │   └── impl/
    └── lambda/
        ├── lambdas/         # Functional interfaces + method refs
        ├── streams/         # Stream API
        ├── optional/        # Optional API
        ├── concurrency/     # Parallel streams
        ├── real/            # Real-world patterns + validation
        └── util/            # Shared models: Car, Brand, Review, Database
```

## Domain Model

All lambda/stream examples operate on a `Car` database of 22 cars with brands (Toyota, Ford, BMW, etc.), prices, years, and reviews.

```java
Car car = Car.builder()
    .brand(Brand.TOYOTA)
    .model("Corolla")
    .price(20000.0)
    .year(2020)
    .reviews(List.of(...))
    .build();
```

## Prerequisites

- Java 16+
- Maven 3.x

## Dependencies

| Library | Version | Purpose |
|---|---|---|
| Lombok | 1.18.38 | `@Data`, `@Builder`, `@AllArgsConstructor` |
| Jackson Databind | 2.19.2 | JSON serialization |

## Build

```bash
mvn clean compile
```

## Running Examples

Each topic has its own main class:

```bash
# Annotations
java com.annotation.AnnotationApplication

# Generics
java com.generic.GenericApp

# Lambdas & functional interfaces
java com.lambda.lambdas.LambdaApplication

# Streams (intermediate + terminal operators)
java com.lambda.streams.StreamApp

# Collectors (grouping, partitioning)
java com.lambda.streams.CollectorApp

# Optional
java com.lambda.optional.OptionalApp

# Real-world patterns (file I/O, strategy, validation, comparators)
java com.lambda.real.RealApp

# Concurrency / parallel streams
java com.lambda.concurrency.ConcurrencyStreamApp
```

Or run all via Maven after packaging:

```bash
mvn package
java -cp target/<jar-name>.jar com.lambda.streams.StreamApp
```
