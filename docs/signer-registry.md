# Signer Registry

The Signer Registry maps signing keys to authorized models. Nano uses it to verify that an intent came from an approved model runtime.

## Key Status

- `active`: key may verify signatures normally.
- `suspended`: temporarily inactive; reject until restored.
- `revoked`: permanently invalid; reject all signatures.

## Rotation State

- `active`: normal use.
- `rotating`: successor key is primary, but this key may still verify in-flight intents during the overlap window.
- `verification_only`: no new signatures should be created with this key, but in-flight signatures may still verify.
- `retired`: no verification accepted.

## Required Enforcement

Nano must verify:

1. The `signing_key_id` exists.
2. The key is not revoked or retired.
3. The key is valid for the evaluation time.
4. The signature algorithm matches the signer registry.
5. The key is authorized for `source_model.model_id`.
6. The public key fingerprint matches the expected value.

## Related File

- `schema/signer-registry.schema.json`
