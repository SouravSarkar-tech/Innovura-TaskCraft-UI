# #See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

# FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
# WORKDIR /app
# EXPOSE 80
# EXPOSE 443

# FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
# WORKDIR /src
# COPY ["InnovuraTaskCraftUI/InnovuraTaskCraftUI.csproj", "InnovuraTaskCraftUI/"]
# RUN dotnet restore "InnovuraTaskCraftUI/InnovuraTaskCraftUI.csproj"
# COPY . .
# WORKDIR "/src/InnovuraTaskCraftUI"
# RUN dotnet build "InnovuraTaskCraftUI.csproj" -c Release -o /app/build

# FROM build AS publish
# RUN dotnet publish "InnovuraTaskCraftUI.csproj" -c Release -o /app/publish /p:UseAppHost=false

# FROM base AS final
# WORKDIR /app
# COPY --from=publish /app/publish .
# ENTRYPOINT ["dotnet", "InnovuraTaskCraftUI.dll"]


# FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env
# WORKDIR /App

# # Copy everything
# COPY . ./
# # Restore as distinct layers
# RUN dotnet restore
# # Build and publish a release
# RUN dotnet publish -c Release -o out

# # Build runtime image
# FROM mcr.microsoft.com/dotnet/aspnet:7.0
# WORKDIR /App
# COPY --from=build-env /App/out .

# EXPOSE 5000

# ENTRYPOINT ["dotnet", "InnovuraTaskCraftUI.dll"]


FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env
WORKDIR /App

# Copy everything
COPY . ./
# Restore as distinct layers
RUN dotnet restore
# Build and publish a release
RUN dotnet publish -c Release -o out

# Build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /App
COPY --from=build-env /App/out .

EXPOSE 5000
CMD ["dotnet", "InnovuraTaskCraftUI.dll", "--urls", "http://0.0.0.0:5000"]
