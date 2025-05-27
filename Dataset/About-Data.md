# 🌱 GBIF Biodiversity Data Analysis

This repository contains biodiversity occurrence data retrieved from the Global Biodiversity Information Facility (GBIF) via their public API. The data will be used for Big Data Analysis tasks, focusing on species conservation status based on IUCN Red List categories.

## 📦 Dataset Description

- **Source:** GBIF.org  
- **Dataset Key:** 3e0987c4-375f-4d68-b2ac-5e4e3a6d3d6d  
- **API Endpoint:** https://api.gbif.org/v1/occurrence/search  
- **Accessed via:** Python requests library  
- **Total Records Retrieved:** All available records in the specified dataset (paginated with limit=300 per request)

## 🔍 Data Fields Extracted

The data retrieved includes numerous fields, but for analysis purposes, one key field of interest is:

- **iucnRedListCategory:** Indicates the conservation status of a species based on the IUCN Red List. Some categories include:

  - **NE:** Not Evaluated (in this context, treated as Near Threatened species)  
  - **LC:** Least Concern  
  - **EN:** Endangered  

## 🧪 Data Processing Workflow

- Fetch all records from the GBIF API using pagination.  
- Combine all results into a single DataFrame.  
- Filter the dataset based on the **iucnRedListCategory**.  
- Export filtered datasets to separate CSV files:  
  - `gbif_NE.csv`  
  - `gbif_LC.csv`  
  - `gbif_EN.csv`

## 📁 Output Files

| File Name     | Description                                      |
|---------------|-------------------------------------------------|
| `gbif_NE.csv` | Species records classified as Near Threatened (NE) — species yang hampir terancam di Indonesia |
| `gbif_LC.csv` | Species records classified as Least Concern (LC) — species dengan risiko konservasi rendah di Indonesia |
| `gbif_EN.csv` | Species records classified as Endangered (EN) — species yang terancam punah di Indonesia |

## 📋 Atribut dan Deskripsi Dataset

| Atribut               | Deskripsi Atribut                                                                                     |
|-----------------------|-----------------------------------------------------------------------------------------------------|
| key                   | ID unik untuk setiap catatan kejadian (occurrence) di GBIF                                          |
| datasetKey            | ID unik dari dataset sumber dalam GBIF                                                              |
| publishingOrgKey      | ID organisasi yang mempublikasikan dataset                                                           |
| installationKey       | ID instalasi sistem data yang digunakan                                                              |
| hostingOrganizationKey| Organisasi yang meng-host data                                                                        |
| publishingCountry     | Negara tempat data dipublikasikan                                                                     |
| protocol              | Protokol metadata yang digunakan                                                                      |
| lastCrawled           | Tanggal terakhir data dikumpulkan oleh sistem GBIF                                                   |
| lastParsed            | Tanggal terakhir data diparsing/ditafsirkan                                                           |
| crawlId               | ID proses pengambilan (crawl) data terakhir                                                          |
| projectId             | ID proyek sumber data                                                                                 |
| programmeAcronym      | Singkatan dari program pendanaan atau kolaborasi (kosong bila tidak ada)                               |
| extensions            | Ekstensi data tambahan (kosong bila tidak ada)                                                       |
| basisOfRecord         | Jenis rekaman dasar, misalnya spesimen yang diawetkan                                                |
| occurrenceStatus      | Status kemunculan, misalnya “PRESENT” berarti spesies benar-benar ditemukan                           |
| taxonKey              | ID spesifik untuk takson yang diobservasi                                                           |
| kingdomKey            | ID kingdom dari spesies                                                                              |
| phylumKey             | ID phylum dari spesies                                                                               |
| classKey              | ID class dari spesies                                                                                |
| orderKey              | ID order dari spesies                                                                                |
| familyKey             | ID family dari spesies                                                                               |
| genusKey              | ID genus dari spesies                                                                                |
| speciesKey            | ID spesies dari spesies                                                                              |
| acceptedTaxonKey      | ID takson yang telah diterima secara ilmiah                                                         |
| scientificName        | Nama ilmiah spesies seperti yang dilaporkan                                                        |
| acceptedScientificName| Nama ilmiah yang diterima oleh taksonomis                                                           |
| kingdom               | Nama klasifikasi kingdom spesies                                                                    |
| phylum                | Nama klasifikasi phylum spesies                                                                     |
| class                 | Kelas taksonomi spesies                                                                              |
| order                 | Nama klasifikasi order spesies                                                                      |
| family                | Nama klasifikasi family spesies                                                                     |
| genus                 | Nama klasifikasi genus spesies                                                                      |
| species               | Nama klasifikasi spesies                                                                            |
| genericName           | Nama genus dari spesies                                                                             |
| specificEpithet       | Nama spesifik dari spesies                                                                          |
| taxonRank             | Tingkat klasifikasi takson                                                                           |
| taxonomicStatus       | Status validasi taksonomi spesies                                                                   |
| iucnRedListCategory   | Status spesies menurut IUCN (NE = Not Evaluated)                                                    |
| decimalLatitude       | Koordinat geografis lokasi spesies ditemukan                                                       |
| decimalLongitude      | Koordinat geografis lokasi spesies ditemukan                                                       |
| continent             | Benua tempat spesimen ditemukan                                                                     |
| gadm                  | Lokasi administratif dalam format GADM (Global Administrative Areas)                                |
| year                  | Tahun pengamatan specimen                                                                           |
| month                 | Bulan pengamatan specimen                                                                           |
| day                   | Hari (tanggal) pengamatan specimen                                                                 |
| eventDate             | Tanggal pengamatan specimen                                                                         |
| startDayOfYear        | Hari (tahun) dimulai pengamatan                                                                    |
| endDayOfYear          | Hari (tahun) selesai pengamatan                                                                    |
| issues                | Permasalahan atau asumsi dalam data, seperti konversi koordinat                                     |
| lastInterpreted       | Tanggal terakhir data diinterpretasikan oleh sistem GBIF                                           |
| license               | Lisensi penggunaan data                                                                             |
| isSequenced           | Menunjukkan apakah spesimen memiliki data DNA                                                      |
| identifiers           | Kode pengenal unik spesimen, dari institusi terkait                                               |
| media                 | Informasi media seperti foto spesimen                                                              |
| facts                 | Informasi tambahan yang relevan dengan spesimen, jika ada                                          |
| relations             | Informasi tambahan yang relevan dengan spesimen, jika ada                                          |
| isInCluster           | Apakah spesimen termasuk dalam kelompok (cluster) tertentu                                        |
| dnaSequenceID         | ID urutan DNA jika tersedia (kosong berarti tidak ada)                                             |
| geodeticDatum         | Sistem referensi koordinat geografis                                                               |
| countryCode           | Kode ISO negara                                                                                    |
| recordedByIDs         | ID pihak yang mengamati/mengidentifikasi spesimen                                                  |
| identifiedByIDs       | ID pihak yang mengamati/mengidentifikasi spesimen                                                  |
| gbifRegion            | Wilayah regional menurut pembagian GBIF                                                           |
| country               | Negara tempat spesimen ditemukan                                                                   |
| publishedByGbifRegion | Wilayah publikasi dataset menurut GBIF                                                             |
| identifier            | Pengenal unik specimen                                                                             |
| dataGeneralizations   | Indikasi bahwa koordinat telah digeneralisasi demi perlindungan data                               |
| locality              | Lokasi umum di mana spesimen ditemukan                                                            |
| gbifID                | ID unik dari catatan di sistem GBIF                                                               |
| occurrenceID          | ID kejadian pengamatan spesimen                                                                   |
| infraspecificEpithet  | Nama varietas atau subspesies jika tersedia                                                       |
| dateIdentified        | Tanggal spesimen diidentifikasi secara taksonomi                                                  |
| identifiedBy          | Nama orang yang mengidentifikasi spesimen                                                        |
| typeStatus            | Status tipe spesimen dalam konteks taksonomi                                                      |

## ⚙️ Requirements

To run the script, you need the following Python libraries:

```bash
pip install requests pandas
