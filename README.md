# Vikas Rathore

Software Engineer at Threecolts, working on distributed systems behind high-volume marketplace
integrations: event-driven microservices processing 1.5M+ webhook events a day.

Most of the work is keeping that pipeline safe to operate. Events arrive at-least-once, so
processing has to be idempotent - a redelivered event lands as a no-op, not a duplicate order.
Ingestion stays separate from processing: a Lambda verifies each webhook's signature, resolves the
merchant and hands the event to a queue, so a slow consumer never blocks intake. Consumers scale
on queue depth and sit behind circuit breakers and dead-letter queues. Sellers are throttled per
tenant - a 100 QPS ceiling on one marketplace, a 1,000-point GraphQL cost budget on the other - so
one bulk upload cannot starve everyone else's sync.

The rest is correctness at the edges. A scheduled sync catches products delisted on the
marketplace side and unlinks them before a seller oversells. Privacy webhooks are answered at the
edge, so compliance traffic never mixes with orders. Every sync runs against a 30-minute SLA, with
p99 and p95 latency tracked daily and every breach traced to its cause.

Java, Python (FastAPI, Celery, Pydantic), PHP (Phalcon), Node.js, TypeScript. AWS: SQS, Lambda,
DynamoDB, S3, CloudWatch, API Gateway, EventBridge. MongoDB, Redis, MySQL. GraphQL, REST,
webhooks, OAuth, RS256 JWT, Docker, GitHub Actions.
