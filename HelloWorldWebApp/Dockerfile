#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS build-env
WORKDIR /app
#copy csproj and restore as distinct Layers
copy *.csproj ./
RUN dotnet restore

# copy everything else and build
copy . ./

RUN dotnet publish -c Release -o out
# build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
COPY --from=build-env /app/out .

ENTRYPOINT ["dotnet", "HelloWorldWebApp.dll"]