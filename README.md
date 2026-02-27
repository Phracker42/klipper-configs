# Klipper Configuration Repository

Structured Klipper configurations for multiple 3D printers. (TAZ 6, Voron V0)

This repository treats each printer as a version-controlled machine asset.

## Supported Printers

| Printer | Board | Compute | Status | Path |
|----------|--------|----------|---------|------|
| Voron V0 | Manta M8P | CB1 | Production | printers/voron-v0/manta-m8p/cb1 |

## Repository Structure

common/      → Shared macros and sensors  
printers/    → Individual printer configs  
scripts/     → Deployment utilities  
docs/        → Wiring diagrams and tuning logs  
templates/   → Base config templates  

## Configuration Architecture

Each printer uses a modular structure:

printer.cfg
 ├── mcu.cfg
 ├── steppers.cfg
 ├── heaters.cfg
 ├── toolhead.cfg
 └── overrides.cfg (local, not version controlled)

Shared macros are included from /common.

## Deployment

Manual copy:

scp -r printers/<printer-path>/* pi@printer-ip:/home/pi/printer_data/config/

Or use:

./scripts/deploy.sh <printer-path>

Restart Klipper after deployment.

## Versioning

main → stable configs  
feature/* → experimental changes  

Tag stable machine states:

git tag v0-stable-YYYY-MM

## Sensitive Files

The following files are excluded from version control:

- secrets.cfg
- wifi.cfg
- overrides.cfg
- moonraker_private.conf

## Tuning Records

Input shaper, PID, and pressure advance records are stored in:

docs/tuning-records/
