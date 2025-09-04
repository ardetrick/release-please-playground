


```mermaid
graph TD
  %% Nodes
  shared["shared-lib"]
  fooservice["foo-service"]
  fooapp["foo-application"]
  barapp["bar-application"]
  bazapp["baz-application"]

  %% Permutation A: lib -> lib -> application
  shared --> fooservice
  fooservice --> fooapp

  %% Permutation B: application with no deps
  %% (bar-application has no incoming edges)

  %% Permutation C: lib -> application
  shared --> bazapp

  %% Styling (optional)
  classDef lib fill:#eef,stroke:#88a,stroke-width:1px;
  classDef app fill:#efe,stroke:#8a8,stroke-width:1px;
  class shared,fooservice lib;
  class fooapp,barapp,bazapp app;

```









```json
{
  "$schema": "https://raw.githubusercontent.com/googleapis/release-please/main/schemas/config.json",
  "release-type": "maven",
  "separate-pull-requests": false,
  "include-component-in-tag": true,
  "include-v-in-tag": true,
  "plugins": [
    {
      "type": "maven-workspace",
      "considerAllArtifacts": true
    }
  ],
  "packages": {
    "shared-lib": {
      "component": "shared-lib",
      "release-type": "maven"
    },
    "foo-application": {
      "component": "foo-application",
      "release-type": "maven"
    }
  }
}

```