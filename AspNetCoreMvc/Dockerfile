# SDK Image �ekiyoruz
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-sdk
# Derleme a�amas� i�in bir klas�r olu�turuyoruz ve �al��ma dizinini ayarl�yoruz
WORKDIR /app

# Sadece proje dosyalar�n� kopyala ve ba��ml�l�klar� geri y�kle
COPY *.csproj . 
RUN dotnet restore

# T�m dosyalar� kopyala
COPY . ./

# Bir s�r�m olu�turun ve yay�nlay�n
RUN dotnet publish AspNetCoreMvc.csproj -c Release -o out

# Yeni images
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS build-runtime
# �al��ma zaman� i�in bir klas�r olu�turuyoruz ve �al��ma dizinini ayarl�yoruz
WORKDIR /app

# �nceki a�amadan (build-sdk) yay�mlanan dosyalar� kopyala
COPY --from=build-sdk /app/out .

# Uygulaman�n hangi portta �al��aca��n� belirt
ENV ASPNETCORE_URLS="http://*:4500"

# Uygulamay� �al��t�rmak i�in giri� noktas�n� belirt
ENTRYPOINT ["dotnet", "AspNetCoreMvc.dll"]


#Bu Dockerfile, �nce geli�tirme ve derleme i�in .NET SDK g�r�nt�s�n� kullanarak projeyi derleyip yay�nlar, 
#ard�ndan daha hafif bir .NET ASP.NET Core g�r�nt�s�nde yay�nlanm�� dosyalar� �al��t�rarak uygulamay� �al��t�r�r.