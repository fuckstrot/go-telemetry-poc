# Telemetry System Improvements

## Priority 1: Core Stability & Maintenance
[ ] Refactor global state (config, loggers) to dependency injection
[ ] Implement structured logging (zap/logrus)
[ ] Add configuration validation (BrokerAddress, CollectionInterval)
[ ] Create graceful shutdown context propagation
[ ] Implement MQTT connection retry logic with backoff
[ ] Add health check endpoint (/health)

## Priority 2: Security & Reliability
[ ] Add TLS support for MQTT
[ ] Implement configuration reload (SIGHUP)
[ ] Add telemetry data persistence (disk buffer during outages)
[ ] Create basic auth for MQTT (username/password)
[ ] Add resource usage limits (max memory/CPU for collector)

## Priority 3: Architectural Improvements
[ ] Modularize components:
    - /pkg/collector (system metrics)
    - /pkg/publisher (MQTT client)
    - /pkg/subscriber (MQTT consumer)
    - /pkg/models (data structures)
[ ] Implement interface-based collectors:
    type Collector interface {
        Collect() (interface{}, error)
    }
[ ] Use channels for telemetry pipeline:
    collector → buffer → publisher

## Priority 4: Performance & Efficiency
[ ] Parallelize process metrics collection (worker pool)
[ ] Implement incremental network stats (deltas instead of absolutes)
[ ] Add selective collection (configurable modules)
[ ] Use object pool for telemetry structs
[ ] Stream JSON directly to MQTT (avoid memory buffering)

## Priority 5: Enhanced Telemetry
[ ] Add disk I/O metrics (read/write ops, latency)
[ ] Implement per-core CPU usage
[ ] Add container/docker metrics
[ ] Collect filesystem metrics per partition
[ ] Add battery status (for mobile/laptops)

## Priority 6: Alerting & Monitoring
[ ] Threshold-based alerting system:
    - CPU > 90%
    - Memory < 10% free
    - Disk > 85% full
[ ] Alert suppression mechanism
[ ] Add Prometheus metrics endpoint (/metrics)
[ ] Implement OpenTelemetry tracing

## Priority 7: Deployment & Operations
[ ] Create Dockerfile for containerization
[ ] Add systemd service file
[ ] Implement version flag (-v/--version)
[ ] Build .deb/.rpm packages
[ ] Add log rotation support

## Priority 8: Testing & Quality
[ ] Unit tests with mocked dependencies (70% coverage)
[ ] Integration test with test MQTT broker
[ ] Benchmark critical collection functions
[ ] Add end-to-end test scenario
[ ] Implement CI/CD pipeline (GitHub Actions)

## Priority 9: User Experience
[ ] Create web dashboard (basic real-time monitoring)
[ ] Add report generation (PDF/HTML)
[ ] Implement configurable output formats (JSON, CSV, Text)
[ ] Add --dry-run mode for testing
[ ] Create interactive CLI with survey library

## Priority 10: Advanced Features
[ ] Cluster-aware deployment mode
[ ] Anomaly detection (statistical baselines)
[ ] Historical data storage (SQLite/TSDB)
[ ] SNMP collector integration
[ ] Windows event log collection

## Technical Debt & Refactoring
[ ] Remove duplicate hostname lookups
[ ] Standardize error handling patterns
[ ] Add JSDoc-style comments for all functions
[ ] Optimize memory allocations in hot paths
[ ] Refactor network collection to avoid double iteration

## Documentation
[ ] Architecture diagram (plantuml/mermaid)
[ ] Configuration reference guide
[ ] Deployment playbook
[ ] Troubleshooting guide
[ ] Metric definitions documentation

## Suggested Implementation Order
1. Dependency injection + structured logging
2. Security fundamentals (TLS, auth)
3. Architectural modularization
4. Performance optimizations
5. Alerting subsystem
6. Extended telemetry sources
7. Deployment packaging
8. UI/Reporting features

# Usage Instructions
- Mark items with [x] when completed
- Add @assignee for team members
- Use !P1, !P2 tags for prioritization
- Add estimates (e.g., #2h) for tasks