FROM mcr.microsoft.com/dotnet/sdk:5.0 as build
WORKDIR /app

COPY "ApiGateway.csproj" "ApiGateway.csproj"
RUN dotnet restore "ApiGateway.csproj"

COPY . .

FROM build as publish
WORKDIR /publish

COPY --from=build /app .
RUN dotnet publish "ApiGateway.csproj" -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as runtime
WORKDIR /app

COPY --from=publish /publish/out .

ENTRYPOINT [ "dotnet", "ApiGateway.dll" ]
