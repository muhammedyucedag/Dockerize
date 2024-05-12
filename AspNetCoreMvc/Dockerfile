# SDK Image çekiyoruz
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-sdk
# Derleme aþamasý için bir klasör oluþturuyoruz ve çalýþma dizinini ayarlýyoruz
WORKDIR /app

# Sadece proje dosyalarýný kopyala ve baðýmlýlýklarý geri yükle
COPY *.csproj . 
RUN dotnet restore

# Tüm dosyalarý kopyala
COPY . ./

# Bir sürüm oluþturun ve yayýnlayýn
RUN dotnet publish AspNetCoreMvc.csproj -c Release -o out



# Yeni images
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS build-runtime
# Çalýþma zamaný için bir klasör oluþturuyoruz ve çalýþma dizinini ayarlýyoruz
WORKDIR /app

# Önceki aþamadan (build-sdk) yayýmlanan dosyalarý kopyala
COPY --from=build-sdk /app/out .

# Uygulamanýn hangi portta çalýþacaðýný belirt
ENV ASPNETCORE_URLS="http://*:4500"

# Uygulamayý çalýþtýrmak için giriþ noktasýný belirt
ENTRYPOINT ["dotnet", "AspNetCoreMvc.dll"]


#Bu Dockerfile, önce geliþtirme ve derleme için .NET SDK görüntüsünü kullanarak projeyi derleyip yayýnlar, 
#ardýndan daha hafif bir .NET ASP.NET Core görüntüsünde yayýnlanmýþ dosyalarý çalýþtýrarak uygulamayý çalýþtýrýr.