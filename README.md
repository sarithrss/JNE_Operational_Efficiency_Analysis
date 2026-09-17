## JNE Operational Efficiency Analysis

## 1. Project Overview
Proyek ini menganalisis 300.000 data pengiriman JNE (Jalur Nugraha Ekakurir) untuk mengidentifikasi inefisiensi operasional, menekan pelanggaran SLA, dan
menurunkan tingkat pengembalian paket (Return to Sender).

Fokus utamanya adalah bagaimana pemahaman terhadap kualitas data dan pola risiko pembayaran dapat dimanfaatkan untuk menurunkan biaya operasional dan 
meningkatkan kepuasan pelanggan, terutama di tengah lonjakan e-commerce dan persaingan logistik yang semakin ketat.

🎯 Key Objectives:
- Objective 1: Mengukur tingkat pelanggaran SLA dan mengidentifikasi akar penyebab keterlambatan antar jenis layanan (REG, YES, OKE).
- Objective 2: Membandingkan tingkat RTS antara metode pembayaran COD vs Prepaid serta menguji signifikansinya.
- Objective 3: Mengidentifikasi kebocoran pendapatan (revenue leakage) akibat anomali data berat dan kualitas data yang buruk.
- Objective 4: Memberikan rekomendasi strategis untuk efisiensi operasional dan peningkatan kualitas data.

## 2. Data Sources
- Dataset 1 (jne_shipments.csv): Data transaksi pengiriman JNE sebanyak 300.000 baris (awb_number, sender_id, origin_branch, dest_city, service_type, payment_type, weight_kg, pickup_date, delivered_date, status).
- Dataset 2 (jne_customers.csv): Data pelanggan sebanyak 30.000 baris (customer_id, city, customer_type).
- Dataset 3 (jne_branches.csv): Data cabang JNE sebanyak 150 baris (branch_code, branch_name, region).

## 3. Technologies Used
- Programming Language: Python (Pandas, NumPy)
- Statistical Analysis: SciPy (Chi-Square Test, Anova)
- Visualization: Matplotlib, Seaborn, Tableau
- Environment: Jupyter Notebook

## 4. Project Structure
📂 jne-operational-analysis
├── 📄 README.md (Summary & Temuan)
├── 📁 data
│   ├── 📥 raw (Dataset Asli)
│   └── 🧹 cleaned (Data Bersih)
├── 📓 notebooks (Proses EDA & Analisis)
├── 📊 reports (Laporan & Dashboard)
│   └── 🖼️ figures (Grafik/Tableau)
├── 📊 PPT_Capstone_JNE.pptx (Slide Presentasi)
├── ⚙️ requirements.txt (Library)
└── 🐍 src (Script Python)

## 📊 5. Summary of Findings

### 💡 5.1 Business Insights
Note: Analisis dilakukan berdasarkan data pengiriman JNE periode 2023 dengan fokus pada efisiensi operasional dan kualitas data.

Aspek Temuan Utama Dampak Bisnis

• Pelanggaran SLA (45,79%): Durasi aktual antar layanan (REG, YES, OKE) hampir identik (±3,5 hari), padahal SLA yang dijanjikan berbeda jauh (YES=1 hari). Layanan premium (YES) tidak benar-benar lebih cepat — masalah kebijakan diferensiasi layanan yang sistemik.
• RTS pada COD (24,96% vs 4,96%): COD terbukti signifikan meningkatkan risiko retur 5x lipat (p-value < 0,05). Estimasi kerugian Rp392.820.000.
• Kebocoran Pendapatan (1.500 data berat anomali / 0,5%): 769 negatif (human error) + 731 nilai 999/9999 (bug timbangan). Estimasi kerugian Rp24.415.000.
• Kualitas Data (15,26% missing customer_type & 2,49% logical error): Menghambat segmentasi cross-selling & mengindikasikan bug scanning barcode.

### 🚀 5.2 Actionable Recommendations
📈 Strategi Operasional — Evaluasi ulang SLA YES agar benar-benar 1 hari, tinjau rute & kapasitas sorting hub.
💳 Manajemen Risiko COD — Verifikasi order & alamat lebih ketat, terapkan blacklist di area RTS tinggi.
💰 Pemulihan Pendapatan — Standarisasi input service_type, perbaiki sistem timbangan, validasi berat negatif.
🤝 Peningkatan Kualitas Data — Lengkapi customer_type, perbaiki sistem scanning barcode.

## 6. Contact
Nama : Sari Theresia
Email : saritheresia88@gmail.com
