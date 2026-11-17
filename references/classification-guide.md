# Classification guide

## Examples

Request: "Add a CSV export button to the existing users table."
- CSV button and escaping of CSV fields: Required / Justified.
- Small utility following existing project patterns: Justified.
- Regression test for exported data: Justified.
- Generic export framework supporting PDF, Excel, XML: Questionable unless existing architecture calls for it.
- User-configurable export scheduling: Out of scope.
- Unrelated table component redesign: Out of scope unless required for integration.

Request: "Fix a login crash when a token expires."
- Handle expired token without crashing: Required.
- Test token expiry and malformed tokens: Justified.
- Replace the entire authentication provider: Questionable, potentially justified only with evidence.
- Redesign login UI: Out of scope unless necessary to handle expiry.

## Distinguish categories
Required is directly specified. Justified is not directly specified but necessary to deliver a safe, maintainable implementation. Questionable means insufficient evidence, not necessarily bad engineering. Out of scope means unrelated or avoidable expansion supported by concrete evidence.

## Risk considerations
Look for migration risk, public API changes, new runtime dependencies, performance impact, and modifications to unrelated subsystems. A large diff is a prompt for investigation, not proof of scope creep.
