FROM mcr.microsoft.com/dotnet/sdk:5.0 as build
WORKDIR /app

COPY "Service2.csproj" "Service2.csproj"
RUN dotnet restore "Service2.csproj"

COPY . .

FROM build as publish
WORKDIR /publish

COPY --from=build /app .
RUN dotnet publish "Service2.csproj" -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as runtime
WORKDIR /app

COPY --from=publish /publish/out .

ENTRYPOINT [ "dotnet", "Service2.dll" ]
