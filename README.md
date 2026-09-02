# AimFlux Auto-Update Repository

This repository is used by the AimFlux Loader for automatic DLL updates.

## How it works

1. The Loader checks `version.json` on startup
2. If the version in `version.json` is newer than the current version, it downloads the new DLL
3. If `force_update` is `true`, the update is mandatory

## How to update

### Step 1: Update the DLL
1. Go to **Releases** → **Create new release**
2. Tag: `v1.0.1` (increment the version)
3. Upload `AimFlux.vmp.dll` as a release asset

### Step 2: Update version.json
Edit `version.json` and update:
```json
{
  "version": "1.0.1",
  "dll_hash": "<sha256_hash_of_new_dll>",
  "dll_download_url": "https://github.com/trungnhan2920-code/auto-update/releases/download/v1.0.1/AimFlux.vmp.dll",
  "changelog": "Updated features...",
  "force_update": true
}
```

### Getting the DLL hash
Run this PowerShell command:
```powershell
(Get-FileHash "AimFlux.vmp.dll" -Algorithm SHA256).Hash.ToLower()
```

## Fields

| Field | Description |
|-------|-------------|
| `version` | Version string (e.g., "1.0.1") |
| `dll_hash` | SHA256 hash of the DLL (for integrity check) |
| `dll_download_url` | Direct download URL from GitHub Releases |
| `changelog` | Description of changes |
| `force_update` | If `true`, users MUST update |
