# escape=`
FROM mcr.microsoft.com/windows/servercore/iis
SHELL [ "powershell" ]

ARG ENV_NAME=DEV

EXPOSE 80

COPY src\template.html C:\template.html
RUN (Get-Content -Raw -Path C:\template.html) `
    -replace '{hostname}', [Environment]::MachineName `
    -replace '{environment}', [Environment]::GetEnvironmentVariable('ENV_NAME') `
    | Set-Content -Path C:\inetpub\wwwroot\index.html