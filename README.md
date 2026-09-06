# LinguaGraph M2 independent hosted proof

This public repository is a checkpoint-scoped, disposable proof harness for the LinguaGraph M2 candidate. It does not modify the application repository or establish permanent CI policy.

## Exact proof target

- Application: `Pacchifans69/LinguaGraph`
- Branch: `m2-linguistic-segmentation-foundation`
- Candidate SHA: `f367f53f0c0de1dcef1f46f62cefbe4fc911d207`
- Candidate tree: `aeddeac9067a710b1c0e473a1c4878f49a3ee79d`
- Frozen M2 contract/base: `59e39ac436d8b1e3b4a29992b80fe72f3be2b13f`

The harness fails closed unless the remote branch, detached checkout, commit tree, proof repository, proof branch, and proof commit all match the recorded values.

## Authority and boundary

A Human approved an M2-specific External Infrastructure Exception after the exact candidate's canonical GitHub Actions run #47 failed before any workflow step started. The exception waives only successful proof on a GitHub-hosted runner.

It does not waive exact provenance, clean hosted Linux execution, Python 3.13, Node 24, PostgreSQL 18, frozen dependencies, Alembic empty-to-`0003` verification, full real-PostgreSQL backend tests with zero skips, frontend lint/typecheck/Vitest/build, Playwright golden path, Unicode blocker, M2 segmentation behavior, cleanup, final tracked-tree integrity, or retained evidence.

## Execution

CircleCI runs `.circleci/config.yml` on a fresh Ubuntu 24.04 machine executor. `scripts/run-m2-proof.sh`:

1. verifies the proof repository and exact application SHA/tree;
2. records OS, runtime, Git and container-image provenance;
3. installs dependencies from frozen lockfiles;
4. migrates a fresh PostgreSQL 18 schema through Alembic `0003` and checks it;
5. runs the complete backend suite and rejects any skipped test;
6. runs frontend lint, typecheck, Vitest and production build;
7. runs Playwright golden-path, Unicode and M2 segmentation specifications;
8. drops the disposable database and verifies the candidate remains unmodified;
9. retains command, environment, test, cleanup and SHA-256 evidence.

A successful run is evidence for a later Gate 2 audit. It does not create or merge a LinguaGraph pull request, close G2-X01, or complete M2 by itself.
