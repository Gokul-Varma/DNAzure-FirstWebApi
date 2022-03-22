##See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.
#
#FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
#WORKDIR /app
#EXPOSE 80
#
#FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
#WORKDIR /src
#COPY ["DevopsProjectAzure/DevopsProjectAzure.csproj", "DevopsProjectAzure/"]
#RUN dotnet restore "DevopsProjectAzure/DevopsProjectAzure.csproj"
#COPY . .
#WORKDIR "/src/DevopsProjectAzure"
#RUN dotnet build "DevopsProjectAzure.csproj" -c Release -o /app/build
#
#FROM build AS publish
#RUN dotnet publish "DevopsProjectAzure.csproj" -c Release -o /app/publish
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "DevopsProjectAzure.dll"]


#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.



FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src
COPY WeatherAPI.csproj ./
RUN dotnet restore 
COPY . .
RUN dotnet build
RUN dotnet publish -c Release -o output

FROM mcr.microsoft.com/dotnet/aspnet:3.1
COPY --from=build /src/output ./
ENV ASPNETCORE_URLS=http://+:80
EXPOSE 80
ENTRYPOINT ["dotnet", "DevopsProjectAzure.dll"]