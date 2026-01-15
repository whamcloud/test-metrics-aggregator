# High-Throughput Metrics Aggregator

## Summary

You have been tasked with building a **high-throughput metrics aggregation
system** in Rust.

The system will be used in performance-sensitive environments where multiple
threads concurrently record metrics. The primary goal is to design a solution
that is **thread-safe**, **highly efficient**, and **scales well under load**
while keeping memory usage predictable.

## Requirements

### Core Functionality

* Record latency metrics using the following API:
  ```rust
  record_latency(service: &str, latency_ms: u64);
  ```
* Aggregate metrics by service
* Periodically flush aggregated metrics (e.g. to stdout, logs, or in-memory
snapshots)

## Performance Constraints

* Extremely high write throughput is expected
* Recording metrics must be fast and non-blocking
* Minimize contention between threads
* The solution must scale with increasing thread count

## Concurrency Requirements

* The implementation must be thread-safe
* Avoid global locks where possible
* Must not block callers for extended periods of time
* Correctness must be preserved under concurrent access

## Constraints

* Use only safe Rust
* Do not rely on global mutable state without synchronization
* Memory usage must remain bounded
* The system must behave correctly under sustained load

## Additional Requirements

* Your source should contain unit and concurrency tests where appropriate
* Tests should validate correctness under concurrent access
* All code must be formatted using the standard formatting tool
* Code must compile without clippy errors

## Design & Reasoning (Required)

* Along with the code, include a document (for example DESIGN.md) explaining:
* The overall concurrency model
* How contention is minimized
* Whether sharding, atomics, or locks are used and why
* Trade-offs between accuracy, performance, and complexity
* Known limitations of the solution

Submissions without a design explanation will not be reviewed.

## Submission

Please fork this repository to your own GitHub account and submit a pull request
to your own repository.

Your pull request should include:

* A clear description of your approach
* Any assumptions or trade-offs made
* Instructions on how to run tests

A link to the pull request can be submitted once it is ready for review.

## Bonus

* Percentile calculations (p50, p95, p99)
* Sharded or lock-minimized implementation
* Prometheus-compatible exporter
* Periodic background flushing with configurable intervals
