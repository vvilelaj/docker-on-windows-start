FROM mcr.microsoft.com/dotnet/core/sdk:2.2-nanoserver-sac2016 AS builder

WORKDIR /src
COPY /src .
RUN dotnet restore; dotnet publish

FROM mcr.microsoft.com/dotnet/core/runtime:2.2-nanoserver-sac2016
WORKDIR /app
COPY --from=builder /src/bin/Debug/netcoreapp2.2/publish .

CMD ["dotnet","HelloWorld.NetCore.dll"]