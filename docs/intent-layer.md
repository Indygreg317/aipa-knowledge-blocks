# Intent Layer

The Intent Layer converts model output into a signed, schema-valid, governance-ready request before Nano evaluates it.

Core principle:

> Payload requests. Registry governs. Nano enforces.

Nano must never govern raw model output. It only evaluates validated intent envelopes.

## Evaluation Order

1. Read envelope metadata only.
2. Check declared `intent_schema_version` is supported.
3. Canonicalize payload using RFC 8785 JSON Canonicalization Scheme.
4. Verify the external signature.
5. Confirm `signing_key_id` is authorized for `source_model.model_id` using the signer registry.
6. Validate the full payload schema.
7. Check expiry policy using the action registry.
8. Apply action registry constraints.
9. Evaluate Nano governance policy.
10. Produce an audit record.

## Trust Boundary

The intent payload never asserts its own validity. Verification is performed externally by Nano using the signed envelope and signer registry.

## Related Schemas

- `schema/intent-envelope.schema.json`
- `schema/action-registry.schema.json`
- `schema/signer-registry.schema.json`
- `schema/audit-record.schema.json`
