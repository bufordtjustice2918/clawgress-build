# Clawgress Build Plan (vyos-build fork)

## Goal
Produce reproducible Clawgress images (ISO/OVA/QCOW2/AMI) aligned to MVPv1 (bind9 RPZ + firewall + policy engine + observability), with Clawgress branding and compliant licensing.

## Scope (MVPv1-aligned)
1) **Base build pipeline**
   - Use vyos-build `current` as baseline
   - Standardize build flavor: `generic`
   - Create a deterministic build.conf for CI/local builds

2) **Package integration**
   - Ensure Clawgress packages (vyos-1x fork) are pulled as the build source
   - Verify bind9 dependency is included in image
   - Add policy engine/CLI binaries and configs (RPZ, named.conf) via package stage

3) **Image outputs**
   - ISO (required)
   - OVA/QCOW2 (if build targets supported)
   - Optional: raw image for AMI import

4) **Branding & legal guardrails**
   - Remove/replace VyOS name/logo in image artifacts and splash
   - Preserve license notices and required attributions
   - Review `LICENSE.artwork` and related assets before distribution

5) **Docs & release**
   - Document build commands + prerequisites
   - Publish artifacts (local path + release targets)

## Deliverables
- `build.conf` template for Clawgress builds
- Documented build steps (local + CI)
- Image artifacts in `/home/kavan/.openclaw/vyos/`
- Branding/attribution checklist

## Estimates
- **4–7 days** of focused work (one engineer) to get MVPv1‑ready ISO build
  - Build pipeline stabilization + mirrors/deps: 1–2 days
  - Wire Clawgress packages + bind9/RPZ defaults: 1–2 days
  - Branding/attribution cleanup + artifact naming: 0.5–1 day
  - Validation (boot, RPZ, policy apply, logs): 0.5–1 day
  - Docs + release workflow: 0.5–1 day
  - Add 1–2 days buffer for upstream build issues

## Risks / Dependencies
- vyos-build changes in `current` branch
- long build times and resource usage
- licensing/branding review required before public distribution
