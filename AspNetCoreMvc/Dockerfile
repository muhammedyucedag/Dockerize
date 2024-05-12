#FROM: Kullan�lacak taban Docker imaj�n� belirtir.
#WORKDIR: �al��ma dizinini Docker i�indeki bir konuma ayarlar.
#COPY: Belirtilen kaynaktan Docker i�indeki bir konuma dosyalar� kopyalar.
#ENTRYPOINT: Docker konteyneri ba�lat�ld���nda �al��t�r�lacak komutu belirtir.

#Image �ekiyoruz
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-env

#Klas�r olu�turuyoruz
WORKDIR /app

# Her �eyi kopyala
COPY /bin/Release/net8.0/publish .

ENTRYPOINT ["dotnet", "AspNetCoreMvc.dll"]