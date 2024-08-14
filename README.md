# Rust Debug Format to JSON Converter

A simple web tool that converts Rust's `Debug` output to JSON, making it easier to work with Rust data structures in JSON format.

URL: https://jimmygchen.github.io/rust-debug-to-json

## Example Conversions

### Enum

```rust
enum MyEnum {
    VariantA { field1: i32, field2: String },
    VariantB(i32, String),
}
```

**Converted JSON:**

```json
{
  "type": "VariantA",
  "enum": "MyEnum",
  "field1": 10,
  "field2": "value"
}
```

**For `MyEnum::VariantB(10, "data")`:**

```json
{
  "type": "VariantB",
  "enum": "MyEnum",
  "values": [10, "data"]
}
```

### Option

```rust
struct MyStruct {
    optional_field: Option<String>,
}
```

**Converted JSON:**

```json
{
  "type": "MyStruct",
  "optional_field": "some value"  // or `null` for `None`
}
```

### Struct with Positional Fields

```rust
struct Slot(u64);
```

**Converted JSON:**

```json
{
  "type": "Slot",
  "values": [13024]
}
```
