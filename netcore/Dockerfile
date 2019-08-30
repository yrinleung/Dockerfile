FROM microsoft/dotnet:2.2-sdk  AS build-env
WORKDIR /app

# copy csproj and restore as distinct layers
COPY . .
RUN dotnet restore && dotnet publish -c Release -o /out

# build runtime image
FROM microsoft/dotnet:2.2-aspnetcore-runtime
WORKDIR /app
EXPOSE 6007
COPY --from=build-env /out .
CMD ["dotnet", "Api.dll"]
