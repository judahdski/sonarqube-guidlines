# Menjalankan Analisis SonarQube

> ⚠️ **_Perhatian Sebelum Menjalankan!_** <br> - Pastikan kamu **sudah berada di branch `Staging`** sebelum menjalankan perintah analisis. <br> - Pastikan juga kamu **sudah mengikuti step-by-step instalasi dan konfigurasi SonarQube for .NET** sebelumnya.

## 1. Jalankan SonarScanner di CLI (Local/PC)

Di **root folder** proyek (UI atau API) jalankan perintah berikut:

```bash
dotnet sonarscanner begin -v:"360.0.1" -k:"<PROJECT_KEY>" -s:"<path_to_SonarQube.Analysis.xml>"
dotnet build
dotnet sonarscanner end
```

#### 📌 Breakdown Command

-   `-k:"<PROJECT_KEY>"`  
    → Project Key yang terdaftar di SonarQube.  
    _(Cek dashboard SonarQube untuk project key-nya)_

-   `-s:"<path_to_SonarQube.Analysis.xml>"`  
    → Path menuju file `SonarQube.Analysis.xml`  
    _(Klik kanan pada file > Copy Path, atau sesuaikan relatif path-nya)_


## 2. Cek Hasil Analisis

Ada dua cara untuk melihat hasil analisis:

#### 🔹 Melalui Dashboard SonarQube

1. Buka browser ke SonarQube Server (`http://192.168.2.220:6500`)
2. Pilih project, misalnya: **IFINTMS UI**
3. Cek hasil analisis: bugs, code smells, vulnerabilities, dll.

#### 🔹 Convert to Excel/PDF (Not Yet)

Export hasil analisis ke Excel melalui **SonarQube Web API** _(fitur ini belum tersedia, akan diupdate nanti)_
