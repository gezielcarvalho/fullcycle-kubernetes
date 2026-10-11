# Delivery and quality

## Work management

Use a GitHub Issue with a clear objective, acceptance criteria, validation,
risks, rollback, and human gates. Track active work in `Personal Portfolio &
Engineering Labs`; use a pull request for reviewable changes.

## Validation expectations

- For Go code, run the relevant format, build, and test commands where
  available.
- For YAML changes, perform syntax and manifest review before considering an
  apply in a separately approved disposable local cluster.
- For documentation-only changes, verify Markdown links and the final tree.

## Pull-request gate

Each pull request should link its issue, report completed acceptance criteria
and validation evidence, disclose documentation impact, describe rollback, and
identify decisions needing human review. Never use passing automation as
authorization to run cluster-changing commands.

## Quality boundary

The repository demonstrates concepts such as requests/limits, rolling updates,
and rollback. Revalidate any claim against the current manifest and a dedicated
local exercise before presenting it as verified behaviour.
