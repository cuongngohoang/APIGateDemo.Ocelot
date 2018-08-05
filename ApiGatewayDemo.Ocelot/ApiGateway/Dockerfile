
FROM microsoft/dotnet:2.1-sdk-nanoserver-1709 AS base
WORKDIR /app
EXPOSE 9000

# FROM microsoft/dotnet:2.1-sdk-nanoserver-1709 AS build
# WORKDIR /src
# COPY ApiGateway/apigateway.csproj ApiGateway/apigateway/
# RUN dotnet restore ApiGateway/apigateway.csproj
# COPY . .
# WORKDIR /src/ApiGateway/apigateway
# RUN dotnet build ApiGateway/apigateway.csproj -c Release -o /app

# FROM build AS publish
# RUN dotnet publish ApiGateway/ApiGateway.csproj -c Release -o /app


FROM microsoft/dotnet:2.1-sdk-nanoserver-1709 AS build
WORKDIR /src
COPY ApiGateway/ApiGateway.csproj ApiGateway/
RUN dotnet restore ApiGateway/ApiGateway.csproj
COPY . .
WORKDIR /src/ApiGateway
RUN dotnet build ApiGateway.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish ApiGateway.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "apigateway.dll"]
