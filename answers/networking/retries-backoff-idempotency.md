# Retries, exponential backoff, and idempotency - when can retrying a request create duplicate data?

[Back to questions](../../README.md#networking)

**Level:** Middle · **Topic:** Networking

## Answer

A timeout can leave an unknown outcome: the server might have committed the operation even though the client never received its response. Retrying a non-idempotent creation or payment can therefore duplicate an effect.

Use a stable idempotency key for the logical operation with a backend that records and reuses the outcome. Reuse that key across retries; generating another key for each attempt defeats deduplication. Define expiration and conflict behavior on the server.

Retry only eligible transient failures with a limit, exponential backoff, jitter, and supported Retry-After handling. Preserve cancellation and avoid independently stacking retries at several layers. HTTP method idempotency concerns the intended effect, not necessarily identical response codes, and server endpoint behavior must honor the claimed contract.

## References

- [HTTP Working Group: idempotent methods and retry semantics](https://httpwg.org/specs/rfc9110.html)
