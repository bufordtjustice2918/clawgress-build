# Clawgress Build Spec (vyos-build fork)

## Build Inputs
- **vyos-build fork:** `clawgress-build` (current branch)
- **vyos-1x fork:** `clawgress` (source tree)
- **Flavor:** `generic`
- **Build type:** `release`
- **Arch:** `amd64`

## Build Config (build.conf)
```
VYOS_BUILD_FLAVOR=generic
VYOS_BUILD_TYPE=release
VYOS_VERSION=clawgress
VYOS_BUILD_ARCH=amd64
VYOS_SOURCE=/path/to/clawgress/vyos-1x
```

## Required Artifacts
- `*.iso` (primary)
- `*.ova` (optional)
- `*.qcow2` (optional)

## MVPv1 Alignment Requirements
1) **bind9 present** in final image
2) **RPZ policy apply** utilities present
3) **Policy CLI/API** accessible from image
4) **Logging enabled** for RPZ hits
5) **Forced DNS + egress firewall** (VyOS config defaults)

## Branding / Legal
- No “VyOS” branding in artifacts or UI
- Replace splash/strings as needed
- Preserve license notices and attributions
- Verify `LICENSE.artwork` constraints

## Validation Checklist
- Boot ISO in VM
- DNS RPZ allowlist blocks non‑allowed domains
- Policy apply reloads bind9 cleanly
- Logs show deny reason labels
- No VyOS branding visible in UI and artifacts
