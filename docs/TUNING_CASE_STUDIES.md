# Detection tuning case studies

These concise examples are based on the supplied tuning log; use the screenshots as the visual evidence.

## Scheduled tasks — T1053.005

A saved `schtasks /Create` alert fired during a normal Microsoft Office Click-to-Run installation/update. The log recorded parent processes `Integrator.exe` and `OfficeClickToRun.exe`. Adding full-path exclusions removed the observed updater activity, and a later Atomic Red Team test still matched. **Trade-off:** a rule with exclusions can be bypassed if an attacker executes with excluded ancestry; do not treat this as a universally safe exclusion.

![Tuning evidence](../assets/screenshots/step7-01-T1053-false-positive.png)

## Registry Run key — T1547.001

Routine `sihost.exe` access triggered frequent Sysmon Event ID 12 activity. Detection was narrowed to Sysmon Event ID 13 (registry value set), which matched the documented simulated persistence write.

## Account discovery — T1087.001

`net localgroup ... /add` launched by the Splunk installer was account modification, not enumeration. Filtering `/add` removed that observed benign installation behavior while test enumeration remained visible. **Trade-off:** other legitimate discovery remains possible.

## Encoded PowerShell — T1059.001

An initial `*-enc*` match missed Atomic Red Team's `-e` abbreviation. Detection coverage was expanded to abbreviated switches and `pwsh.exe`, then the same test was rerun and observed.

## LSASS via `comsvcs` — T1003.001

Broad Event ID 10 LSASS access matched 45 routine events in a 15-minute window. A more specific process command line (`rundll32.exe`, `comsvcs`, `minidump`) reduced that specific noise and detected the documented test. **Trade-off:** this narrower pattern does not detect all credential dumping.

## Follow-up validation

The original tuning log leaves normal-use activities unchecked, so extended baseline coverage should be treated as **pending** rather than complete.
