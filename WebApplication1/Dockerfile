FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

COPY ./WebApplication1/WebApplication1.csproj ./WebApplication1/
WORKDIR /src/WebApplication1
RUN dotnet restore


COPY ./WebApplication1/ ./
RUN dotnet publish -c Release -o /app/publish /p:PublishTrimmed=false

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app


ENV ASPNETCORE_URLS=http://0.0.0.0:8080


COPY --from=build /app/publish ./

EXPOSE 8080


ENTRYPOINT ["dotnet", "WebApplication1.dll"]
