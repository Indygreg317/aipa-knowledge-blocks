# Audit Record

The Audit Record is the minimum forensic event produced by Nano when evaluating an intent.

Nano should produce an audit record for every accept, reject, queue, block, or escalation decision when the action registry requires audit logging.

## Required Purpose

The audit record must allow a reviewer to reconstruct:

- what intent was evaluated,
- what model and key were involved,
- what registry versions were active,
- what runtime mode was active,
- what decision Nano made,
- why the decision was made,
- and whether the audit chain remains intact.

## Related File

- `schema/audit-record.schema.json`
