#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

# syntax=docker/dockerfile:1
#FROM mcr.microsoft.com/dotnet/core/sdk:5.0 AS build-env
FROM mcr.microsoft.com/dotnet/sdk:5.0-buster AS build
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
#FROM mcr.microsoft.com/dotnet/core/aspnet:5.0
FROM mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim AS base
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "HelloWorldWebApp.dll"]