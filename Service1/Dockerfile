FROM mcr.microsoft.com/dotnet/core/sdk:3.1 as build
WORKDIR /app
EXPOSE 5000

COPY "Service1.csproj" "Service1.csproj"
RUN dotnet restore "Service1.csproj"

COPY . .

FROM build as publish
WORKDIR /publish

COPY --from=build /app .
RUN dotnet publish "Service1.csproj" -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 as runtime
WORKDIR /app

COPY --from=publish /publish/out .

ENV ASPNETCORE_URLS="http://0.0.0.0:5000"

ENTRYPOINT [ "dotnet", "Service1.dll" ]
