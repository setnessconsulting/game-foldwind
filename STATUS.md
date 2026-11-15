# Repository status — Foldwind

**Last updated:** 2026-11-15 (public identity renamed to Foldwind)
**Main:** `c24a04d42d9d09c3e71a4dd587858dee13fd08fd`
**Jira epic:** [GAME-486](https://setnessconsulting.atlassian.net/browse/GAME-486)
**Child map:** [docs/jira-map.md](docs/jira-map.md)
**Name decision:** [docs/name-search.md](docs/name-search.md)

The game and repository were renamed from Skyfold to Foldwind after a public
name search found a same-genre SkyFold game and a SKYFOLD REPUBLIC trademark
filing. The implementation is unchanged.

## State

**Lifecycle:** foundation / grey-box prototype. There is no public build.

| Capability | State | Evidence |
|---|---|---|
| Public repo and Godot 4.7.2 project | Implemented | `project.godot`; clean-clone import |
| Deterministic flight simulation | Implemented and verified | `scripts/sim/flight_sim.gd`; 34 tests / 90 checks |
| Tap flap + hold glide | Implemented and verified | Grey-box; headless tests |
| Gates, thread/graze scoring, combo | Implemented and verified | Headless tests |
| Instant restart and pause | Implemented | Grey-box scene |
| Headless verification | Implemented and verified | `tools/ci/verify.ps1`; 38 project checks |
| CI `game-pr-fast` | Verified on PRs #1-#4 | Required check; latest run on the exact PR head |
| Export templates | Installed and verified | `4.7.2.stable` Windows templates |
| Windows export smoke | Implemented; not clean-VM qualified | `build/windows/Foldwind.exe` + `.pck`; exported runtime 300-frame smoke |
| Final art and audio | Not started | — |
| Campaign, Endless, Daily | Not started | — |
| Saves and accessibility | Not started | — |
| Windows export and release | Not started | — |

## Verification

Canonical command:

```powershell
.\tools\ci\verify.ps1
```

Current evidence is repository-only. It does not qualify feel, visual quality,
audio, accessibility, performance on a clean Windows VM, or a release. See
[docs/evidence/gate-0.md](docs/evidence/gate-0.md).

## Jira state

The epic and 34 children exist. All children are in Backlog. Gate 0 work is
being implemented in the repository; statuses will move only as evidence is
recorded. SF-05's human five-session feel gate is pending, so Gate 0 is not
complete.

## Merge gate

`main` is protected by a strict required `game-pr-fast` check from GitHub
Actions App 15368, with zero approving reviews and no force pushes or deletions.
Jenkins is not a required check.

## Open work

1. Five internal grey-box sessions and the SF-05 go/no-go memo.
2. Paper Fields vertical slice and five external players.
3. Gate 1 go/no-go decision.

Then systems, art, audio, content, verification, and the Windows release follow
in [docs/epic-foldwind.md](docs/epic-foldwind.md).
