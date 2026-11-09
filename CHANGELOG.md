# Changelog

All notable changes to TubeSonic are documented here.

## [1.4.2] — 2026-11-09

### Fixed
- Progress bar freezing on long playlist conversions
- Incorrect bitrate label shown for M4A output
- Rare crash when the output folder was removed during a conversion

### Changed
- Faster audio encoding pipeline (up to ~15% quicker on multi-core CPUs)
- Updated bundled codec libraries

## [1.4.1] — 2026-10-18

### Fixed
- Duplicate queue entries when pasting the same link twice
- Tray icon not restoring correctly after sleep mode

### Added
- `clipboard_watch` option in `settings.json`

## [1.4.0] — 2026-09-02

### Added
- Batch queue with parallel conversions
- Filename templates (`{artist} - {title}`, track numbering)
- Automatic cover art embedding

### Changed
- Redesigned dark UI
- New settings file format (`config/settings.json`)

## [1.3.0] — 2026-07-14

### Added
- M4A and WAV output formats
- Volume normalization option

## [1.2.0] — 2026-05-21

### Added
- First public release
- MP3 conversion with up to 320 kbps
- Drag & drop link support
