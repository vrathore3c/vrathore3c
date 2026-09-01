# Vikas Rathore

Software Engineer at Threecolts. Backend work on high-volume, event-driven marketplace
integrations.

- At-least-once delivery means every webhook can arrive twice. Idempotent processing with
  per-state keys and atomic upserts makes the second delivery a no-op.
- Circuit breakers and dead-letter queues keep one degraded downstream API from stalling the whole
  pipeline; consumers autoscale on queue depth.
- Per-seller rate limiting and backpressure stop one tenant's bulk upload from starving every other
  seller's sync.
- Eventual consistency is measured, not assumed: p95 and p99 sync latency tracked against an SLA,
  every breach attributed to its cause.

1.5M+ events a day. Java, Python, PHP and Node.js on AWS, MongoDB, Redis.
