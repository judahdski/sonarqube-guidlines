# Setup SonarScanner for .NET

> ℹ️ **SonarScanner for .NET** <br> Tool yang akan membaca kode C#, lalu menganalisa kode itu dan mengirim hasil analisisnya ke **SonarQube Dashboard**.

## 1. Instalasi SonarScanner

Jalankan perintah di bawah ini di Command Line:

```bash
dotnet tool install --global dotnet-sonarscanner
```

Verifikasi Instalasi. Cek apakah sudah terinstal dengan:

```bash
dotnet tool list --global
```

Jika berhasil, maka akan muncul daftar tool global yang terinstal, termasuk `dotnet-sonarscanner`.

---

## 2. Tambahkan Konfigurasi di Proyek UI & API

Di root folder proyek masing-masing, tambahkan file `SonarQube.Analysis.xml` dengan isi seperti berikut:

### 📁 UI Project

```xml
<?xml version="1.0" encoding="utf-8" ?>
<SonarQubeAnalysisProperties xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                             xmlns:xsd="http://www.w3.org/2001/XMLSchema"
                             xmlns="http://www.sonarsource.com/msbuild/integration/2015/1">
  <Property Name="sonar.host.url">http://192.168.2.220:6500</Property>
  <Property Name="sonar.token">[token]</Property>

  <Property Name="sonar.inclusions">Program.cs,Components/**/*.cs,Pages/**/*.cs</Property>
  <Property Name="sonar.scanner.scanAll">false</Property>
</SonarQubeAnalysisProperties>
```

### 📁 API Project

```xml
<?xml version="1.0" encoding="utf-8" ?>
<SonarQubeAnalysisProperties xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                             xmlns:xsd="http://www.w3.org/2001/XMLSchema"
                             xmlns="http://www.sonarsource.com/msbuild/integration/2015/1">
  <Property Name="sonar.host.url">http://192.168.2.220:6500</Property>
  <Property Name="sonar.token">[token]</Property>

  <Property Name="sonar.inclusions">/API/**/*.cs,/DAL/**/*.cs,/Domain/**/*.cs,/Service/**/*.cs</Property>
  <Property Name="sonar.exclusions">/API/Program.cs</Property>
  <Property Name="sonar.scanner.scanAll">false</Property>
</SonarQubeAnalysisProperties>
```

---

## 3. Tambahkan ke `.env` File

Tambahkan entri berikut ke file `.env`:

```env
# sonarqube
SonarQube.Analysis.xml
.sonarqube/
```

---

## ✅ Selesai!

Selanjutnya, lanjutkan ke penggunaan SonarQube via CLI.

📄 Referensi lengkap bisa kamu lihat di [Confluence Page (akses internal)](https://judahjmdasuki.atlassian.net/wiki/spaces/~632d2861409249995ee848ee/pages/2392096)
