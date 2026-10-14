# Architecture and methodology

## Environment

- Oracle VirtualBox hosted one Windows 11 VM, `Target-VM`.
- Supplied report: 8 GB RAM, 4 vCPUs, 100 GB virtual disk. EFI enabled.
- Sysmon installed with a lab configuration; Sysmon Operational events were collected locally.
- Splunk Enterprise ran **inside the same VM**, created index `sysmon`, and collected the Windows channel directly using `inputs.conf` (`renderXml = true`). This is not a multi-host SOC and does not use a separate Splunk Universal Forwarder.
- VirtualBox snapshots supported recovery between simulations.

## Pipeline

1. Controlled user activity and Atomic Red Team tests created telemetry.
2. Sysmon logged processes and registry changes to `Microsoft-Windows-Sysmon/Operational`.
3. Splunk ingested XML events into index `sysmon`.
4. SPL searches extracted and filtered relevant events.
5. Saved searches/alerts were exercised and reviewed against test traffic.
6. Rules were tuned to reduce observed benign false positives.
7. Results were mapped to ATT&CK subtechniques.

## Parsing failure and workaround

The build log reports **38,061** ingested Sysmon events while an `EventCode` breakdown initially returned nothing. The data was present, but the field was not extracted for that search. An inline expression demonstrated the EventID in raw XML:

```spl
index=sysmon
| rex "<EventID>(?<EventCode>\d+)</EventID>"
| stats count by EventCode
```

A custom `props.conf` / `transforms.conf` approach was attempted because a Splunk Sysmon add-on was unavailable. The source build log has an unfinished note about the final permanent configuration; therefore this repository **does not claim the field-extraction configuration was fully resolved**. The SPL samples include an inline extraction where needed.

## Safe test methodology

All simulations must be confined to a disposable VM under your control. Capture a snapshot before changes, run one Atomic Red Team technique at a time, inspect resulting Sysmon events, compare to SPL detection, execute cleanup, and restore/review baseline. Where a technique is blocked by Defender, document that separately rather than counting it as an unqualified success.
