# Azure Stack HCI with AKS and Datadog
Steps to recreate an Azure Stack HCI homelab with AKS and Datadog Network Monitoring

## Manual Steps

The following describes the manual install you'd do on a host/server prior to imaging if using a traditional "golden image" workflow:

Windows Host Script for *BETA* NPM-Enabled Datadog Agent
```powershell
client = new-object System.Net.WebClient
client.DownloadFile("https://s3.amazonaws.com/ddagent-windows-unstable/datadog-agent-7.23.2-beta1-1-x86_64.msi","C:\tmp\datadog.msi")
Start-Process -Wait msiexec -ArgumentList '/qn /i c:\temp\datadog.msi APIKEY="<YOUR_DATADOG_API_KEY>"'
"$env:ProgramFiles\Datadog\Datadog Agent\bin\agent.exe" launch-gui
notepad c:\ProgramData\Datadog\datadog.yaml
notepad c:\ProgramData\Datadog\system-probe.yaml
restart-service -f datadogagent
```

For WIM-based setups, most of this can (and should!) be scripted. The System Probe and Datadog YAML files in this repo can be used as a starting point, but you'll probably want to create your own bootstrap fils and scripts in a private location.
