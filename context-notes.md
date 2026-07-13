# Portfolio Context Notes

## 2026-07-13

- Nginx is a directly managed Docker reverse-proxy container, not a Kubernetes Ingress controller.
- The architecture view uses data-flow direction for Kafka and request/dependency direction for service calls.
- Channel Engine does not call Event Persist Worker directly. The event path is Channel Engine to Kafka to Event Persist Worker to MariaDB.
- Redis is shared by sessions and read/member caches. AI rate limiting is not presented as active production behavior.
- AWS and Kubernetes deployment details are not represented as completed infrastructure in this logical architecture view.
- The desktop canvas height reserves space for the header, legend, and two architecture notes so the complete board fits in a typical laptop viewport.
- Static verification confirmed UTF-8 integrity, unique core view IDs, valid inline JavaScript syntax, and a clean `git diff --check` result.
- Direct `file://` visual inspection was unavailable because the in-app browser blocks local file URLs. GitHub Pages rendering remains the final visual check after push.
