# Action Registry

The Action Registry defines which actions are allowed, how they are routed, and what constraints Nano must enforce.

Core principle:

> The payload is a request. The registry governs.

If a payload conflicts with the registry, the registry wins.

## Evaluation Hierarchy

1. Signer Registry gates source authority.
2. Intent Schema validates structure.
3. Action Registry governs allowable behavior.
4. Nano Policy evaluates runtime conditions.
5. Safety Layer overrides emergency physical constraints.
6. Audit Layer records all accept, reject, queue, block, and escalation decisions.

## Example Behaviors

- If `autonomous_allowed` is false, Nano must not allow autonomous execution.
- If `requires_safety_layer` is true and the safety layer is unavailable, Nano blocks execution.
- If `requires_zone_clearance` is true and personnel are nearby, Nano blocks autonomous execution.
- If the system is in `DEGRADED_MODE`, Nano applies `degraded_mode_behavior`.

## Related Files

- `schema/action-registry.schema.json`
- `examples/intent-governance/action-registry-industrial-line2.json`
