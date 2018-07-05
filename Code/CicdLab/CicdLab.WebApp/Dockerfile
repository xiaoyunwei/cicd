FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
COPY CicdLab.WebApp/CicdLab.WebApp.csproj CicdLab.WebApp/
RUN dotnet restore CicdLab.WebApp/CicdLab.WebApp.csproj
COPY . .
WORKDIR /src/CicdLab.WebApp
RUN dotnet build CicdLab.WebApp.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish CicdLab.WebApp.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "CicdLab.WebApp.dll"]
