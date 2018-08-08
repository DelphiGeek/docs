# Benchmark Results Schema

* Updated: 2018 August 9

[TOC]

This document describes the JSON schema that Fuchsia benchmark results must follow in
order to upload to the performance dashboard.

## JSON Description

```json
[
    {
        "label":       "string",  // Name of the test case in the performance dashboard.
        "test_suite":  "string",  // Name of the test suite in the performance dashboard.
        "unit":        "string",  // One of the supported units (see below)
        "values":      [number],  // Values collected in this test case
        "split_first": bool       // Whether to split the first element in |values| from the rest.
    },
    {
        ...
    }
]
```

## Supported Units:

* `nanoseconds`
* `milliseconds`
* `seconds`
* `bytes`

## split_first behavior

When `"split_first"` is true, benchmark results will appear as two separate series in the
performance dashboard:

1. `$label/samples_0_to_0` which tracks the first element in Values, and
1. `$label/samples_0_to_N` which tracks the remaining values.

## Implementation

Rather than write code to produce this JSON yourself, you can use one of the existing
Fuchsia libraries for your language:

* C/C++: [//zircon/system/ulib/perftest]
* Go: [//garnet/go/src/benchmarks]
* Dart: [TODO(kjharland)](#)
