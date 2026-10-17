# .NET (stack rules)

Copy as-is into .NET projects. Project facts still go in `../project/stack.md`.

## Build output

- Keep agent build and restore intermediate output in the fixed repository-root path
  `TEMP/codex-build`: `dotnet build <solution> --artifacts-path .\TEMP\codex-build`.
- Reuse that path on every run; do not create a new output directory per run.
- Never place custom build output under a project directory. MSBuild can copy it back
  into its own output and create recursive artifact trees.
- Do not clean or reuse the IDE's normal `bin/obj` directories for agent verification.

## NuGet restore and package cache

- Use the NuGet cache already configured in the environment. Its location or account
  name (including `CodexSandboxOffline`) alone is not a reason to block a build.
  Normal restore of the existing dependencies is allowed.
- Do not remove dependencies, change package versions, edit NuGet configuration,
  clear or relocate package caches, or overwrite the IDE's normal build/restore
  metadata as a workaround for verification. Such changes require a separate user request.
- Do not redirect package caches into `TEMP/`, the repository, or a per-task directory.
  Build-output isolation covers compiled and intermediate output, not downloaded packages.
