# Azure Stack HCI with AKS and Datadog
Steps to recreate an Azure Stack HCI homelab with AKS and Datadog Network Monitoring

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
