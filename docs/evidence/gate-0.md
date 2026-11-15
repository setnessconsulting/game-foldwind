# Gate 0 evidence - foundation and grey-box

**Recorded:** 2026-11-15 (America/Los_Angeles)
**Final Gate 0 main:** `c24a04d42d9d09c3e71a4dd587858dee13fd08fd`
**Engine:** Godot `4.7.2.stable.official.ed1daf0bf`
**Renderer:** GL Compatibility
**Repository:** `setnessconsulting/game-foldwind`
**Epic:** GAME-486

**Rename note:** The public identity was Skyfold at the original Gate 0
checkpoint. It was renamed to Foldwind on 2026-11-15 after the name search
found a same-genre SkyFold game and a SKYFOLD REPUBLIC trademark filing. The
technical evidence below is unchanged; GitHub redirects the old repository URL.

**Pull requests in this gate:** #1 Game Maker profile, #2 Windows export and
pck filters, #3 public identity rename, #4 version/badge/Jira-map closeout.

## What was verified

| Check | Command | Result |
|---|---|---|
| Import | `godot --headless --path . --import` | Pass |
| Full local verification | `.\tools\ci\verify.ps1` | Pass |
| GDScript parse check | `godot --headless --path . --check-only --script <each .gd>` | Pass |
| Headless core tests | `godot --headless --path . --script res://tests/run_tests.gd` | **34 tests, 90 checks, 0 failures** |
| Project verification | `godot --headless --path . --script res://tools/verify_project.gd` | **38 checks, 0 failures** |
| Runtime smoke | `godot --headless --path . --quit-after 300` | No runtime errors |
| Movie Maker render | `godot --path . --resolution 1280x720 --write-movie <png> --fixed-fps 60 --quit-after 90` | 90 frames rendered; frame reviewed |
| Export templates | Exact Godot 4.7.2 Windows templates installed under the editor template directory | `version.txt` = `4.7.2.stable` |
| Windows export smoke | `godot --headless --path . --export-release "Windows Desktop" build/windows/Foldwind.exe` | Pass; `Foldwind.exe` + 32,596-byte `Foldwind.pck` |
| Exported runtime smoke | `build/windows/Foldwind.exe --headless --quit-after 300` | Exit 0, no runtime errors |
| CI gate | GitHub Actions `game-pr-fast` on PRs #1-#4 | Pass on every exact PR head |
| Branch protection | Live `main` protection | Strict `game-pr-fast` from App 15368; zero approvals |

The movie render used the RTX 4070 Laptop GPU. It is a presentation smoke test,
not a performance qualification.

## Game Maker metadata

- `docs/game-maker-profile.json` was generated with the `project-game-maker`
  profile model and round-trips through `GameProjectProfile.from_dict`.
  Profile hash: `sha256:e1eca3c8d60a85395b41b784d0007c333ffd28b973e601c2596958d654b4b4ec`.
- The profile binds `setnessconsulting/game-foldwind`, GAME-486, the Gate 0
  work scope, `windows`, the Godot 4.7.2 tool profile, and the 60 fps / 300 MB
  quality budgets.
- The optional `GodotToolchainDeclaration` is not generated. The current
  `godot-toolchain-v1` parser rejects Godot's multiline `[input]` action
  values. This is a declared-metadata tool limitation, not a live-execution
  claim.

## What this does not prove

- Human feel, fun, or readability. SF-05's five internal sessions are still
  pending.
- Final art or audio. The grey-box is intentionally placeholder.
- Campaign, Endless, Daily, saves, or accessibility.
- Clean-VM behavior, SmartScreen, code signing, or a public release. The export
  smoke ran on the development machine.
- Performance on Intel Iris Xe. The render used the discrete GPU.

## Next evidence

1. Five internal grey-box sessions and the SF-05 go/no-go memo.
2. The Paper Fields vertical slice and five external players.
3. The Gate 1 go/no-go decision.
