# Usamos la imagen base de .NET 9.0
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /app

# Copiamos
COPY . .

# Restauramos y publicamos el proyecto
# Nota: Ajusta "NombreDeTuProyecto.csproj" si tu archivo tiene otro nombre.
RUN dotnet publish "./Proyecto_despliegue/Proyecto_despliegue" -c Release -o out

# Imagen final para ejecutar la app
FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app/out .

ENTRYPOINT ["dotnet", "Proyecto_despliegue.dll"]