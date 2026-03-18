# App Manifest

## Status

The current Core implementation uses a JSON `manifest.json` per app install root. The richer app-runtime model is no longer just a draft direction inside Core; it is the practical contract that `AppsManager` validates and compiles into launch policy.

The YAML example in Core is still useful as explanatory documentation, but it is not the runtime format that `AppsManager` parses today.

## Canonical Format Today

Current production-facing format:

* file name: `manifest.json`
* encoding: JSON object
* install location: one manifest per app directory

Example install layout:

* `/opt/thecube/apps/<app-id>/manifest.json` in system mode
* `<CubeCore executable directory>/apps/<app-id>/manifest.json` in local/dev mode

## Top-Level Shape

The current Core manifest contract uses these top-level sections:

* `schema_version`
* `app`
* `runtime`
* `permissions`
* `environment`
* optional `ui`

## `app` Section

Current expected fields:

* `id`
* `name`
* `version`
* `vendor`
* `description`
* `category`
* `args` optional
* `working_directory`
* `type`
* `autostart`
* `system_app`

Notes:

* `id` must match Core's app ID validation rules.
* `working_directory` must resolve inside the install root.
* `system_app: true` and `autostart: true` affect startup behavior.

## `runtime` Section

Runtime types currently recognized by Core:

* `native`
* `python`
* `node`
* `docker`
* `web-bundle`

Current implementation status:

* `native`: supported
* `python`: supported
* `node`: supported structurally
* `docker`: supported
* `web-bundle`: recognized, but not launchable yet

Runtime-specific fields:

* `runtime.native.entrypoint`
* `runtime.python.entry_script`
* `runtime.python.package_name` optional
* `runtime.node.entry_script`
* `runtime.docker.image`

Common lifecycle fields currently carried in the manifest:

* `restart_policy`
* `max_restart_burst`
* `restart_window_seconds`
* `stop_timeout_seconds`
* `start_timeout_seconds`

## `permissions` Section

Current manifest validation requires:

* `permissions.filesystem.read_only`
* `permissions.filesystem.read_write`

Other supported sections:

* `permissions.platform`
* `permissions.network`

### Filesystem tokens supported today

App-scoped tokens:

* `app://install`
* `app://assets`
* `app://data`
* `app://cache`
* `app://runtime`

Shared read-only token:

* `shared://readonly/<relative-path>`

Host system token:

* `system://<relative-host-path>`

Examples:

* `system://usr`
* `system://lib`
* `system://usr/share/zoneinfo`
* `system://tmp`
* `system://proc`

Important rule:

* `system://...` exists so apps must explicitly request host path access rather than inheriting broad system readability from the launcher

## `environment` Section

Supported fields:

* `allow_inherit`
* `set`

At launch time, Core also injects:

* `THECUBE_APP_ID`
* `THECUBE_DATA_DIR`
* `THECUBE_CACHE_DIR`
* `THECUBE_RUNTIME_DIR`
* `THECUBE_CORE_SOCKET`

## Launch Policy Relationship

The manifest is not the final launch contract. `AppsManager` compiles the manifest into a resolved `launch-policy.json` that contains:

* resolved `argv`
* working directory
* resolved executable path
* environment
* Landlock read-only/read-write/create paths
* platform and network metadata

That generated launch policy is what `CubeAppLauncher` actually consumes.

## Example

```json
{
  "schema_version": "1.0",
  "app": {
    "id": "com.example.weather-clock",
    "name": "Weather Clock",
    "version": "0.2.1",
    "vendor": "Example Vendor",
    "description": "Displays the time and weather on TheCube.",
    "category": "utility",
    "args": ["--theme=mono"],
    "working_directory": ".",
    "type": "interactive",
    "autostart": false,
    "system_app": false
  },
  "runtime": {
    "type": "python",
    "distribution": "venv",
    "compatibility": "3.11",
    "python": {
      "entry_script": "main.py",
      "package_name": "weather_clock"
    },
    "restart_policy": "on-failure",
    "max_restart_burst": 5,
    "restart_window_seconds": 60,
    "stop_timeout_seconds": 10,
    "start_timeout_seconds": 15
  },
  "permissions": {
    "platform": [
      "display.basic",
      "display.foreground",
      "network.http_client"
    ],
    "filesystem": {
      "read_only": [
        "app://install",
        "app://assets",
        "shared://readonly/weather/icons",
        "system://usr/share/zoneinfo"
      ],
      "read_write": [
        "app://data",
        "app://cache",
        "app://runtime"
      ]
    },
    "network": {
      "allow": true,
      "inbound": false,
      "domains": [
        "api.weather.gov",
        "time.google.com"
      ],
      "local_network": false
    }
  },
  "environment": {
    "allow_inherit": [],
    "set": {
      "THECUBE_LOCALE": "en-US",
      "TZ": "UTC"
    }
  }
}
```

## What Is Not Implemented Yet

These should not be documented as active production manifest features unless Core implementation changes:

* cgroup/resource-control sections
* secrets materialization sections
* event pub/sub manifest sections
* arbitrary fine-grained sandbox sections beyond the current filesystem/network/platform model
* YAML manifest parsing in `AppsManager`

## Open Items

* `Decision needed:` decide whether YAML remains documentation-only or becomes a first-class manifest input format.
* `Open question:` define how manifest schema versioning will be enforced as the platform grows.
* `Needs verification:` update this doc whenever the internal launch-and-sandbox doc or `AppsManager` validation rules change.

## Sources

* Local: `Companion-TheCube---Core/src/apps/the_cube_app_launch_and_sandboxing_plan.md`
* Local: `Companion-TheCube---Core/src/apps/exampleApp.manifest.json`
* Local: `Companion-TheCube---Core/src/apps/exampleApp.manifest.yml`
* Local: `Companion-TheCube---Core/src/apps/appsManager.cpp`
