
FROM microsoft/dotnet:2.1-sdk-nanoserver-1709 AS base
WORKDIR /app
EXPOSE 9003

FROM microsoft/dotnet:2.1-sdk-nanoserver-1709 AS build
WORKDIR /src
COPY Api3/api3.csproj Api3/
RUN dotnet restore Api3/api3.csproj
COPY . .
WORKDIR /src/Api3/api3
RUN dotnet build Api3/api3.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish Api3/api3.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "api3.dll"]
