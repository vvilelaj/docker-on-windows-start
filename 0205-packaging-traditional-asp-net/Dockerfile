
FROM mcr.microsoft.com/dotnet/framework/sdk:4.7.2 as builder

# restore packages
WORKDIR /src/NerdDinner
COPY /src/NerdDinner/packages.config .
RUN nuget restore packages.config -PackagesDirectory /src/packages

# generate Nerdinner package  
COPY /src /src
RUN msbuild ./NerdDinner.csproj /p:Configuration=Release /p:OutDir=/out

FROM mcr.microsoft.com/dotnet/framework/aspnet:4.7.2
SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop';"]
WORKDIR /nerd-dinner-webapp
RUN Remove-Website -Name 'Default Web Site'; \
    New-Website -Name 'nerd-dinner-webapp' -Port 80 -PhysicalPath 'C:\nerd-dinner-webapp' -ApplicationPool '.NET v4.5'
RUN & /windows/system32/inetsrv/appcmd.exe unlock config /section:system.webServer/handlers

COPY --from=builder /out/_PublishedWebsites/NerdDinner ./