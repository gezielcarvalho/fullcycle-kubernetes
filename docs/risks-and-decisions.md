# Risks and decisions

## Active risks

| Risk | Impact | Response |
| --- | --- | --- |
| A command targets the wrong kubectl context. | Resources could change outside the intended lab. | Inspect and confirm the context before any separately approved action. |
| Learning manifests are treated as production-ready. | Missing security, observability, or release controls. | Keep the local-lab boundary explicit and require a dedicated environment decision. |
| Dashboard or Portainer admin access is exposed beyond the lab. | Unnecessary cluster privilege or exposure. | Use only locally, with ephemeral access, and never treat included setup as production guidance. |
| Image or dependency versions drift. | Demos and exercises stop reproducing. | Revalidate prerequisites and update through tracked review. |

## Decision log

| Date | Decision | Rationale |
| --- | --- | --- |
| 2026-10-11 | Retain the progressive course documentation as the detailed learning source. | It is the repository's core educational value. |
| 2026-10-11 | Define Kind/WSL as the only supported operating posture. | No approved production environment is documented. |
