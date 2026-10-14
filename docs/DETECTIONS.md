# Detection rationale

Five ATT&CK-mapped subtechniques are demonstrated in the supplied lab report and screenshots. Examples in `detections/splunk/` are **reconstructed portfolio searches based on the documented observed rules**; check them against your current sourcetype and field extraction before deploying. They are not presented as production-ready rules.

| File | Intent | Tuning caveat |
|---|---|---|
| `T1053_005_scheduled_task.spl` | Process creation of scheduled tasks | Excludes observed Office Click-to-Run parents; verify they cannot be abused in your environment |
| `T1547_001_run_key.spl` | Registry Run key value written | Sysmon Event ID 13 (set), not benign Event ID 12 open |
| `T1087_001_account_discovery.spl` | Local accounts enumeration | Filters `/add` activity, but admin use of `net user` can still be legitimate |
| `T1059_001_encoded_powershell.spl` | Encoded PowerShell command execution | Detects abbreviated flags and `pwsh.exe`; can still miss variations |
| `T1003_001_comsvcs_lsass.spl` | `rundll32`+`comsvcs` MiniDump pattern | Focused high-signal technique, not generic LSASS access |

## Interpretation of the five alerts

Evidence reports the simulated behavior triggered detections, including saved Splunk alerts. This does not quantify accuracy, cover untested variants, or establish a false-positive rate over normal use. See [Tuning case studies](TUNING_CASE_STUDIES.md) and [Limitations](LIMITATIONS.md).
