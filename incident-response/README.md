# Incident responder

Run the local webhook receiver from the repository root:

```bash
python3 incident-response/responder.py
```

It listens on `127.0.0.1:8001` and accepts Grafana-compatible webhook payloads at `POST /alerts`.
For every firing alert it stores evidence in `incident-response/evidence/<incident-id>/` and starts `codex exec` in headless mode. The special `ResponderTest` payload uses Codex's read-only sandbox and must finish with `RESPONDER_TEST_ACKNOWLEDGED`.

The responder is intentionally not included in `compose.yaml`; Grafana webhook wiring belongs to Question 6.
