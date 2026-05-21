# Bug Log

Use this file as Codex's reusable memory for bugs the user wants to avoid repeating.

## How To Search

- Search by project/module names: `fyc-effectrenderer`, `Unity`, `Editor`, `Runtime`, `Shader`.
- Search by technology tags: `csharp`, `odin`, `asmdef`, `materialpropertyblock`, `unity-package`.
- Search by symptoms: exact exception text, compiler errors, failed test names, visual artifacts.

## Entries

### 2026-05-21 - Dynamic Instancing Materials Fail On Device

- Context: Unity runtime rendering, materials with GPU instancing support, especially effects rendered on real devices.
- Symptom: A material dynamically created at runtime and configured to support instancing works in editor or local testing but fails on device.
- Trigger: Creating instancing-capable materials dynamically instead of using materials authored and serialized offline.
- Root cause: Runtime-created instancing material setup is not reliable on device; offline-created material assets preserve the required shader/material state.
- Fix: Create the instancing material offline as a Unity asset and reference that asset at runtime.
- Prevention rule: Before adding runtime material creation for instanced rendering, require an offline-created material asset path/reference and avoid relying on dynamic `new Material(...)` setup for device builds.
- Verification: User-reported device behavior; validate future fixes on real device builds, not only in editor.
- Tags: `unity`, `csharp`, `runtime`, `material`, `instancing`, `device`, `effectrenderer`
- Seen again: 0
