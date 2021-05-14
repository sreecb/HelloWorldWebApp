#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/sdk:5.0
WORKDIR /app
COPY . .
ENV ASPNETCORE_URLS http://*.5000
EXPOSE 5000
ENTRYPOINT ["dotnet", "HelloWorldWebApp.dll"]