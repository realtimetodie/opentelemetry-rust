# OpenTelemetry-Rust

[![Crates.io: opentelemetry](https://img.shields.io/crates/v/opentelemetry.svg)](https://crates.io/crates/opentelemetry)
[![Documentation](https://docs.rs/opentelemetry/badge.svg)](https://docs.rs/opentelemetry)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE.txt)

A Rust [OpenTelemetry](https://opentelemetry.io/) client.

## Quick Start

```rust
use opentelemetry::{api::{Provider, TracerGenerics}, global, sdk};

fn main() {
    let tracer = sdk::Provider::new().get_tracer("service_name");
    global::set_tracer(Box::new(tracer));

    global::global_tracer().with_span("foo", || {
        global::global_tracer().with_span("bar", || {
            global::global_tracer().with_span("baz", || {

            })
        })
    });
}
```

See the [opentelemetry-example-app](./example/basic.rs) for a complete example.

## Release Schedule

OpenTelemetry Rust is under active development. Below is the release schedule for the Rust library. The first version
of a release isn't guaranteed to conform to a specific version of the specification, and future releases will not
attempt to maintain backwards compatibility with the alpha release.

| Component                   | Version | Target Date     |
| --------------------------- | ------- | --------------- |
| Tracing API                 | Alpha   | November 8 2019 |
| Tracing SDK                 | Alpha   | November 8 2019 |
| Metrics API                 | Alpha   | November 8 2019 |
| Metrics SDK                 | Alpha   | November 8 2019 |
| Zipkin Trace Exporter       | Alpha   | Unknown         |
| Jaeger Trace Exporter       | Alpha   | November 8 2019 |
| Prometheus Metrics Exporter | Alpha   | November 8 2019 |
| Trace Context Propagation   | Alpha   | Unknown         |
| OpenTracing Bridge          | Alpha   | Unknown         |
| OpenCensus Bridge           | Alpha   | Unknown         |
