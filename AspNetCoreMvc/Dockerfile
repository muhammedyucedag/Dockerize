#FROM: Kullanýlacak taban Docker imajýný belirtir.
#WORKDIR: Çalýþma dizinini Docker içindeki bir konuma ayarlar.
#COPY: Belirtilen kaynaktan Docker içindeki bir konuma dosyalarý kopyalar.
#ENTRYPOINT: Docker konteyneri baþlatýldýðýnda çalýþtýrýlacak komutu belirtir.

#Image çekiyoruz
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env

#Klasör oluþturuyoruz
WORKDIR /app

# Her þeyi kopyala
COPY /bin/Release/net8.0/publish .

ENTRYPOINT ["dotnet", "AspNetCoreMvc.dll"]
