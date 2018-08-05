FROM microsoft/dotnet AS base
WORKDIR /app2
EXPOSE 9002

FROM microsoft/dotnet:2.1-sdk-nanoserver-1709 AS build
WORKDIR /src1
COPY Api2/api2.csproj Api2/
RUN dotnet restore Api2/Api2.csproj
WORKDIR /src1/Api2/Api2
COPY . .
RUN dotnet build Api2/Api2.csproj -c Release -o /app2

FROM build AS publish
RUN dotnet publish Api2/Api2.csproj -c Release -o /app2

FROM base AS final
WORKDIR /app2
COPY --from=publish /app2 .
ENTRYPOINT ["dotnet", "api2.dll"]
