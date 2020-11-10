FROM mcr.microsoft.com/dotnet/sdk:5.0 as build
WORKDIR /app

COPY "Service1.csproj" "Service1.csproj"
RUN dotnet restore "Service1.csproj"

COPY . .

FROM build as publish
WORKDIR /publish

COPY --from=build /app .
RUN dotnet publish "Service1.csproj" -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as runtime
WORKDIR /app

COPY --from=publish /publish/out .

ENTRYPOINT [ "dotnet", "Service1.dll" ]
