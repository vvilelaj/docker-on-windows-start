FROM mcr.microsoft.com/dotnet/core/runtime:2.2-nanoserver-sac2016

WORKDIR /dotnetapp
COPY ./src/bin/Debug/netcoreapp2.2/publish .

CMD ["dotnet", "HelloWorld.NetCore.dll"]