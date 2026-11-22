# OmniBand desktop update roadmap

**Planning date:** 2026-11-23
**Current public release:** 1.0.4
**Next planned update:** 1.0.5 — proposed
**Scope:** Windows desktop application only. This page tracks shipped work and follow-up plans; it is not a release package.

## Delivered in 1.0.4

### Download reliability

- Resume segmented transfers only when the server confirms the requested byte range and the file representation can be validated safely.
- Bound retry attempts and backoff, distinguish temporary network failures from permanent HTTP or local-storage errors, and show useful failure reasons without exposing signed URLs or credentials.
- Preserve verified partial work after pause or interruption and verify the assembled file before completing it.

### Downloads workspace

- Bring status, category, and queue navigation together with a searchable, sortable downloads list.
- Keep manual URL entry in the Downloads workflow and put the per-download connection default in Settings.
- Make common task actions available from the selected row and keep transfer details available without crowding the main list.

### Network and Settings

- Show benchmark and active-download rates as distinct measurements, with a time-based graph and per-adapter detail.
- Distinguish an idle connection, a test waiting for data, and a measured zero rate.
- Group Settings by user task and offer saved main-window scale and download-row density choices.

## Current implementation status

OmniBand 1.0.4 is published with the first implementation pass: stricter segmented-resume and retry handling, clearer transfer failures, a timestamped benchmark/transfer throughput graph, distinct idle and no-data states, improved Downloads navigation and actions, inline manual URL entry, and saved workspace scale and row-density preferences. The release was built as a self-contained Windows installer and portable ZIP; the signed CRX and unpacked extension are included in each app package. These changes are not a claim that every transfer scenario has been proven. Deterministic protocol coverage, real-network checks, visual review across Windows display scales, and install/uninstall acceptance remain follow-up work.

## Remaining validation

- Exercise range handling, changed validators, partial recovery, retries, cancellation, adapter loss, and disk-write failures against a deterministic local HTTP server.
- Compare downloaded output byte-for-byte with controlled source files and verify that cancellation leaves no active workers.
- Confirm benchmark values reconcile with received bytes and elapsed time; verify no-data, waiting, and idle states.
- Review install, extension setup, uninstall, existing task/settings migration, and update behavior on a clean Windows profile.
- Review the UI at the supported minimum window size and Windows display scales, including saved scale and row-density preferences.
- Exercise install, extension setup, uninstall, and fresh reinstall on a clean Windows profile.

## Research basis

- [RFC 9110](https://www.rfc-editor.org/rfc/rfc9110.html) defines HTTP range responses and representation validators; it motivates strict range and resume checks but does not prove OmniBand's implementation is correct.
- The [aria2 manual](https://aria2.github.io/manual/en/html/aria2c.html) separates per-download splits from concurrent downloads; Microsoft's [transient-fault guidance](https://learn.microsoft.com/en-us/azure/architecture/best-practices/transient-faults) describes bounded retries and backoff. These inform the design, while OmniBand still needs its own measurements to choose defaults.
- [IDM's main-dialog guide](https://register.internetdownloadmanager.com/support/using_idm/using_idm.html) documents a familiar toolbar, category navigation, sorting, and row actions. It is a workflow reference, not proof of usability for OmniBand.
- [Cloudflare's speed-test method](https://speed.cloudflare.com/about) distinguishes transfer throughput, first-byte latency, and jitter. OmniBand's adapter-bound measurements must be validated independently.
- Cleveland and McGill's [graphical-perception research](https://doi.org/10.1080/01621459.1984.10478080) supports comparing values with aligned positions on a shared scale; it does not choose OmniBand's visual style.
- Microsoft's [WPF layout](https://learn.microsoft.com/en-us/dotnet/desktop/wpf/advanced/layout) and [high-DPI guidance](https://learn.microsoft.com/en-us/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) motivate separate app scaling and Windows display scaling, with mixed-DPI visual checks still required.

## Planned for 1.0.5 and beyond

The proposed playback-triggered video format panel follows as a later feature update. Each provider needs a source-policy review and format-specific validation before support is enabled; technical access to a stream is not permission to download it.
