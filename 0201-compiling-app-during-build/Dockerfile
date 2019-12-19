FROM mcr.microsoft.com/dotnet/core/sdk:2.2-nanoserver-sac2016

WORKDIR /src
COPY src/ .
RUN dotnet restore
RUN dotnet build

CMD ["dotnet", "run"]