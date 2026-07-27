# SAP Analytics Cloud COVID-19 Dashboard

Business Intelligence dashboard developed using **SAP Analytics Cloud (SAC)** as part of the **ASEAN Data Science Explorers (ADSE) 2026** program.

---

## Overview

Pada proyek ini saya menggunakan **SAP Analytics Cloud (SAC)** untuk membangun dashboard interaktif menggunakan dataset **COVID-19 Global** yang disediakan pada program ASEAN Data Science Explorers.

Dataset berisi berbagai informasi mengenai perkembangan pandemi COVID-19, seperti:

- New Cases
- Total Cases
- New Tests
- Deaths
- Vaccinations
- Population
- GDP
- Human Development Index (HDI)
- dan berbagai indikator sosial ekonomi lainnya.

Melalui proyek ini saya mempelajari bagaimana proses **Business Intelligence** dilakukan menggunakan SAP Analytics Cloud, mulai dari membangun **Data Model**, membuat **Interactive Dashboard**, melakukan **Data Exploration**, hingga menyajikan insight dalam bentuk visualisasi yang mudah dipahami.

---

# Dashboard

🔗 **SAP Analytics Cloud Story**

https://aseandse.ap11.hcs.cloud.sap/sap/fpa/ui/tenants/2bd89/bo/story/D381F076C4B88AF5479575A857D6EE4

🔗 **SAP Analytics Cloud Data Analyzer**

https://aseandse.ap11.hcs.cloud.sap/sap/fpa/ui/tenants/2bd89#view_id=dataAnalyzer;insightId=4CE877806FD6136DFF9F46E7D1C57EB0

> **Note**
>
> Dashboard hanya dapat diakses menggunakan akun SAP Analytics Cloud yang memiliki izin pada tenant ADSE.

---

# Repository Structure

```text
SAP-Analytics-Cloud-COVID19-Dashboard
│
├── README.md
│
├── screenshots
│   ├── dashboard-overview.png
│   ├── data-model.png
│   ├── top5-new-cases.png
│   ├── top5-new-tests.png
│   ├── time-series.png
│   ├── asean-dashboard.png
│   └── data-analyser.png
│
└── assets
```

---

# What I Did

Selama mengerjakan proyek ini saya membuat beberapa komponen utama pada SAP Analytics Cloud, yaitu:

- Data Modeling
- Story Dashboard
- Interactive Charts
- Ranking Visualization
- Time Series Visualization
- KPI Indicator
- Forecasting
- ASEAN Dashboard
- Data Analyzer
- Dashboard Styling

---

# Data Modeling

Hal pertama yang saya lakukan adalah membangun **Data Model** dari dataset Excel.

Pada tahap ini saya mempelajari konsep **Measures** dan **Dimensions**.

- **Measures** merupakan data numerik yang dapat dihitung, misalnya:
  - Total Cases
  - New Cases
  - New Tests
  - Population
  - GDP

- **Dimensions** merupakan data kategorikal yang digunakan untuk mengelompokkan data, misalnya:
  - Country
  - Date
  - Location

Salah satu bagian yang paling penting adalah melakukan konfigurasi **Exception Aggregation**.

Secara default SAP Analytics Cloud akan menjumlahkan seluruh nilai pada setiap baris. Untuk variabel **total_cases**, perilaku tersebut menghasilkan nilai yang tidak sesuai karena data tersebut bersifat kumulatif.

Oleh karena itu saya mengubah konfigurasi menjadi:

- Exception Aggregation : **Last**
- Exception Aggregation Dimension : **Date**

Dengan konfigurasi tersebut SAP hanya mengambil nilai **terakhir** berdasarkan tanggal sehingga jumlah total kasus menjadi lebih akurat.

Selain itu saya juga mengubah variabel **Population** dari **Dimension** menjadi **Measure**, karena Population merupakan data numerik yang seharusnya dapat dihitung dan digunakan pada proses analisis.

![Data Model](screenshots/data-model.png)

---

# Top 5 Countries by New Cases

Pada visualisasi pertama saya membuat **Bar Chart** untuk menampilkan **5 negara dengan jumlah New Cases tertinggi**.

Saya menggunakan fitur:

- Rank → Top 5
- Exclude

Kategori seperti:

- World
- Europe
- Asia
- European Union
- North America
- South America

dihapus menggunakan fitur **Exclude** sehingga grafik hanya menampilkan data berdasarkan negara dan hasil visualisasi menjadi lebih mudah dibaca.

![Top 5 New Cases](screenshots/top5-new-cases.png)

---

# Top 5 Countries by New Tests

Visualisasi kedua dibuat dengan cara **Duplicate** dari grafik sebelumnya.

Cara ini memungkinkan seluruh pengaturan seperti:

- Rank
- Filter
- Styling

tetap digunakan sehingga saya hanya perlu mengganti **Measure** dari:

```
new_cases
```

menjadi

```
new_tests
```

Hasilnya adalah grafik yang menampilkan **Top 5 Countries by New Tests**.

![Top 5 New Tests](screenshots/top5-new-tests.png)

---

# Time Series Analysis

Selanjutnya saya membuat **Time Series Chart** untuk melihat perkembangan jumlah kasus COVID-19 berdasarkan waktu.

Pada tahap ini saya:

- mengubah jenis visualisasi menjadi **Time Series**
- menggunakan **Date** sebagai sumbu waktu
- menghapus kategori **Location** pada bagian Color agar grafik lebih mudah dibaca

Visualisasi ini membantu melihat pola kenaikan dan penurunan kasus dari waktu ke waktu.

Selain itu saya juga mencoba fitur **Automatic Forecast** yang tersedia pada SAP Analytics Cloud.

Fitur ini secara otomatis membuat proyeksi berdasarkan data historis sehingga pengguna dapat memperoleh gambaran mengenai kemungkinan tren pada periode berikutnya.

![Time Series](screenshots/time-series.png)

---

# KPI Indicator

Saya juga membuat **Numeric Point Indicator** untuk menampilkan indikator utama (KPI) secara ringkas.

Visualisasi ini cocok digunakan untuk menampilkan nilai agregat seperti:

- Total New Tests
- Total Cases
- atau indikator penting lainnya

sehingga pengguna dapat langsung melihat informasi utama tanpa harus membaca keseluruhan grafik.

![Dashboard](screenshots/dashboard-overview.png)

---

# ASEAN Dashboard

Selain dashboard global, saya membuat halaman khusus untuk kawasan **ASEAN**.

Saya menggunakan **Page Filter (Input Control)** sehingga dashboard hanya menampilkan data dari:

- Indonesia
- Malaysia
- Singapore
- Thailand
- Philippines
- Vietnam
- Brunei
- Cambodia
- Laos
- Myanmar
- Timor Leste

Dengan fitur ini pengguna dapat membandingkan perkembangan COVID-19 antar negara ASEAN tanpa perlu membuat dashboard baru.

![ASEAN Dashboard](screenshots/asean-dashboard.png)

---

# Data Analyzer

Selain membuat dashboard, saya juga mencoba fitur **Data Analyzer**.

Data Analyzer memungkinkan proses analisis dilakukan secara interaktif tanpa harus membuat Story terlebih dahulu.

Pada bagian ini saya melakukan beberapa eksplorasi data seperti:

- memilih Dimension dan Measure
- melakukan Sorting dari nilai tertinggi ke terendah
- melakukan Filtering
- melakukan Exclude pada kategori **World**
- melihat data dalam bentuk Pivot Table

Fitur ini sangat membantu ketika ingin melakukan eksplorasi data secara cepat sebelum membuat dashboard.

![Data Analyzer](screenshots/data-analyser.png)

---

# Dashboard Styling

Agar dashboard lebih nyaman digunakan, saya juga melakukan beberapa penyesuaian tampilan seperti:

- mengubah warna background
- mengubah font
- mengubah ukuran angka
- mengurangi jumlah angka desimal
- mengatur tata letak setiap visualisasi

Dengan proses ini dashboard menjadi lebih rapi dan informasi lebih mudah dipahami.

---

# What I Learned

Melalui proyek ini saya mendapatkan pengalaman menggunakan **SAP Analytics Cloud** sebagai platform Business Intelligence.

Beberapa hal yang saya pelajari antara lain:

- Data Modeling
- Measures & Dimensions
- Exception Aggregation
- Story Dashboard
- Interactive Charts
- Ranking
- Filtering
- Time Series Analysis
- Automatic Forecast
- KPI Indicator
- Data Analyzer
- Dashboard Styling

Selain belajar membuat visualisasi, saya juga memahami bahwa kualitas dashboard sangat dipengaruhi oleh proses data modeling. Data yang sudah dimodelkan dengan benar akan menghasilkan visualisasi yang lebih akurat dan lebih mudah dipahami oleh pengguna.

---

# Skills

- SAP Analytics Cloud (SAC)
- Business Intelligence
- Data Modeling
- Data Visualization
- Dashboard Development
- Interactive Dashboard
- Data Storytelling
- Time Series Analysis
- Forecasting
- KPI Dashboard
- Data Analytics

---

# Reflection

Melalui proyek ini saya menjadi lebih memahami bagaimana proses Business Intelligence dilakukan menggunakan SAP Analytics Cloud.

Saya belajar bahwa membuat dashboard bukan hanya tentang membuat grafik yang menarik, tetapi juga memahami struktur data, memilih visualisasi yang tepat, melakukan filtering, serta menyajikan informasi agar lebih mudah dipahami oleh pengguna.

Pengalaman ini memberikan gambaran mengenai bagaimana SAP Analytics Cloud digunakan untuk mendukung proses analisis data dan pengambilan keputusan berbasis data di lingkungan bisnis.
