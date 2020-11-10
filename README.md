# GatewayOnContainers

Sample project.

## How to configure HTTPS?

1. Go through articles "Hosting ASP.NET Core images with [Docker](https://docs.microsoft.com/en-us/aspnet/core/security/docker-https) or [Docker Compose](https://docs.microsoft.com/en-us/aspnet/core/security/docker-compose-https)".
```
dotnet dev-certs https -ep %USERPROFILE%\.aspnet\https\aspnetapp.pfx -p { password here }
dotnet dev-certs https --trust
```
2. Add `"DangerousAcceptAnyServerCertificateValidator": true` in your Route config ([Ocelot - SSL Errors](https://ocelot.readthedocs.io/en/latest/features/configuration.html#ssl-errors)).
3. Set `ASPNETCORE_Kestrel__Certificates__Default__Password` and `ASPNETCORE_Kestrel__Certificates__Default__Path` environment variables.
