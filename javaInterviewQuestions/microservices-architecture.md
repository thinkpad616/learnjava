# Microservices Architecture (Study Guide + Examples)

## Contents
- Principles and trade-offs
- Service boundaries and data ownership
- REST vs gRPC vs GraphQL
- API gateway and BFF
- Service discovery (Eureka/Consul), Config Server
- Load balancing and circuit breakers
- Distributed tracing and logging
- Asynchronous messaging (Kafka/RabbitMQ)
- Idempotency, outbox pattern, saga
- Versioning and backward compatibility
- Security basics (OAuth2/OpenID Connect)

---

## REST vs gRPC vs GraphQL
REST: resource-based. gRPC: binary, HTTP/2, contract-first. GraphQL: client-driven queries.

## Gateway
Central entry for auth, rate limiting, routing, aggregation.

## Resilience
Circuit breakers, timeouts, retries with backoff.
