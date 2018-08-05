FROM microsoft/dotnet AS base
WORKDIR /app
EXPOSE 9001

FROM microsoft/dotnet:2.1-sdk-nanoserver-1709 AS build
WORKDIR /src
COPY Api1/Api1.csproj Api1/
RUN dotnet restore Api1/Api1.csproj
WORKDIR /src/Api1/Api1
COPY . .
RUN dotnet build Api1/Api1.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish Api1/Api1.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "Api1.dll"]
