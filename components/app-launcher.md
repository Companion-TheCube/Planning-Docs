# App Launcher

## Purpose

`CubeAppLauncher` is the narrow execution wrapper used by TheCube app runtime flow.

It is a separate application from Core and sits between `systemd` and the target app:

**CubeCore -> systemd -> CubeAppLauncher -> app**

## Current Responsibilities

`CubeAppLauncher` is not an app manager and not a second Core. Its job is to take a resolved launch policy and turn that into one concrete process execution.

Current launcher responsibilities:

* locate and load `launch-policy.json`
* validate the policy structure enough to execute safely
* collect `argv`
* apply the curated environment
* create declared runtime directories
* apply Landlock filesystem restrictions on Linux
* `execve()` the resolved app command

## Policy Input

The launcher consumes a generated launch policy, not the raw app manifest.

Default policy path:

* system mode: `/run/thecube/launch/<app-id>/launch-policy.json`
* local/dev mode: `<CubeCore executable directory>/run/thecube/launch/<app-id>/launch-policy.json`

It can also be invoked directly with:

* `<app-id>`
* `--launch-root <path>`
* `--policy <path>`
* `--trace`
* `--no-landlock`

## Relationship to Core

Core owns:

* manifest discovery
* manifest validation
* runtime preparation
* launch policy compilation
* systemd lifecycle requests

The launcher owns:

* last-step execution setup
* environment application
* Landlock enforcement
* final `execve()`

This keeps the security-sensitive pre-exec logic centralized while leaving broader lifecycle orchestration in Core.

## Landlock Model

The launcher reads `filesystem.landlock` from the launch policy:

* `read_only`
* `read_write`
* `create`

Behavior today:

* it creates all `create` directories before confinement
* it skips Landlock for `docker` runtime entries
* it implicitly allows only a small set of launch-required paths such as the resolved executable parent and working directory
* it does not auto-grant broad system readability like `/usr`, `/lib`, `/etc`, or `/proc`

That means apps needing host paths must declare them through manifest permissions, which Core resolves into launch-policy filesystem entries.

## Runtime Notes

### Native, Python, and Node

The launcher executes the resolved `argv` exactly as compiled by Core.

For Python and Node apps, this often means the launcher executes:

* a managed interpreter path as `argv[0]`
* the app script as the launch target

### Docker

For Docker apps, Core resolves a `docker run ...` command into `argv`.

The launcher still applies environment and executes the resolved command, but it skips Landlock because the sandbox boundary is expected to be provided by the container runtime.

## Why It Stays Separate

Keeping the launcher as a separate executable still makes sense for the current architecture because it provides:

* a small audit surface for pre-exec sandbox logic
* one consistent launch path across app types
* clean separation between policy compilation and policy enforcement
* the ability to test launcher behavior independently of Core startup

## Current Gaps

The launcher is functional, but there are still follow-up areas:

* stricter ownership and integrity validation of launch-policy files
* tighter documentation of failure modes and exit codes
* continued review of implicit path allowances
* broader systemd hardening around the transient app units that invoke it

## Open Items

* `Decision needed:` keep the launcher as a separate component or fold it into Core later. Current recommendation: keep it separate.
* `Open question:` how much policy validation should live in the launcher versus remaining exclusively in Core.
* `Needs verification:` update this doc when the launcher policy contract or CLI changes.

## Sources

* Local: `App-Launcher/src/app_launcher.cpp`
* Local: `Companion-TheCube---Core/src/apps/appsManager.cpp`
* Local: `Companion-TheCube---Core/src/apps/the_cube_app_launch_and_sandboxing_plan.md`
