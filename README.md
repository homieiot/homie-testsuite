# testsuite

testsuite for homie client libraries

this is under early development

## Purpose

This test suite is intended for coders who write homie compatible software to quickly get a solid set of tests to run against their implementations.

The main goal being consistent behaviour across clients.

## Format

The testsuite provided multiple YAML testset files containing test definitions.
The data format of these files is described in the following chapters.

### Testset

A YAML file containing a set of tests to be run. A testset contains the following fields:

- **`description`** (required): A string providing a brief explanation of the testset and its contained tests.
- **`tests`** (required): A list of `test` definitions (see next chapter)

#### Example:

```yaml
description: validating boolean values

tests:
  - ...test definition ...
  - ...test definition ...
  - ...test definition ...
```

### Test

Defines a specific test to be executed. A test consist of the following fields:

- **`description`** (required): A string providing a brief explanation of the test case or the scenario it represents.
- **`testtype`** (required): A string indicating the type of the property value or data being tested. Valid values are:
  - propertyformat
  - propertyvalueinteger
  - propertyvalue
  - homieid
  - ...
- **`definition`**(optional depending on `type`): The test definition (this can for example be a property, node or device descriptions).
- **`input_data`**(optional depending on `type`): The input data provided for the test, which may be represented as a string or other formats, depending on the `type`.
- **`output_data`**(optional depending on `type`): The expected result after processing the `input_data`. This field is typically represented in the correct data type (e.g., `integer` for an integer test).
- **`valid`**(required): A boolean indicating whether the defined test is supposed to pass (true) or fail (false)

#### Example

Here’s an example of how the data looks in practice:

```yaml
description: Normal integer value without format works
type: propertyvalueinteger
definition:
  datatype: integer
input_data: "12"
output_data: 12
valid: true
```
