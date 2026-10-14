# Screenshot evidence index

The following artifacts are a curated subset of a larger screenshot collection from the supplied project. Captions describe their role in the workflow, not claims of unseen activity.

| Evidence | What it demonstrates |
|---|---|
| [VirtualBox install](../assets/screenshots/step1-02-virtualbox-installed.png) | Hypervisor preparation |
| [VM settings](../assets/screenshots/step1-03-vm-settings.png) | Target environment configuration |
| [Sysmon install](../assets/screenshots/step2-02-sysmon-install.png) | Endpoint telemetry deployment |
| [Splunk inputs.conf](../assets/screenshots/step4-01-inputs-conf.png) | Sysmon Windows event channel ingestion configuration |
| [Events flowing](../assets/screenshots/step4-02-events-flowing.png) | Ingested telemetry and a parsing issue |
| [Atomic Red Team installed](../assets/screenshots/step5-02-art-installed.png) | Test tooling readiness |
| [Scheduled task simulated](../assets/screenshots/step5-03-T1053-run.png) | Controlled task-creation test |
| [Task detection SPL](../assets/screenshots/step5-04-T1053-splunk.png) | Matching process-creation telemetry |
| [Account enumeration hit](../assets/screenshots/step6-09-T1087-detection-hit.png) | Local account discovery detection |
| [Encoded PowerShell hit](../assets/screenshots/step6-13-T1059-detection-hit.png) | Encoded execution search result |
| [LSASS alert created](../assets/screenshots/step6-18-T1003-alert-saved.png) | Saved alert setup |
| [LSASS alert triggered](../assets/screenshots/step6-19-T1003-alert-fired.png) | Detected MiniDump test behavior |
| [Scheduled-task false positive](../assets/screenshots/step7-01-T1053-false-positive.png) | Office installer activity contributing to noise |
| [Tuned Sigma rule](../assets/screenshots/step7-03-T1053-sigma-tuned.png) | Revised detection logic documented |
| [ATT&CK layer](../assets/screenshots/step8-01-attack-coverage.png) | Mapped detection coverage |

Review every image at full resolution before publishing to a public repository. Source filenames and explanatory narratives follow the supplied project materials.
