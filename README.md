# 🛡️ OmniScan

<p align="center">

# 🔥 OmniScan

### Multi-Target Passive Web Security Scanner + AI-Powered Security Report

**Scan • Analyze • Understand • Report**

</p>

<p align="center">

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge\&logo=python)
![Security](https://img.shields.io/badge/Security-Authorized%20Testing-red?style=for-the-badge\&logo=hackthebox)
![Mode](https://img.shields.io/badge/Default%20Mode-Passive-green?style=for-the-badge)
![AI](https://img.shields.io/badge/AI-Report%20Analysis-purple?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge)

</p>

---

## ⚡ Overview

**OmniScan** adalah security scanning framework berbasis Python yang dirancang untuk membantu proses pengujian keamanan aplikasi web secara terstruktur.

OmniScan memiliki dua workflow utama:

```text
┌─────────────────────────────────────────────────────────────┐
│                         OMNISCAN                            │
├─────────────────────────────┬───────────────────────────────┤
│                             │                               │
│       SINGLE SCAN           │          MASS SCAN            │
│                             │                               │
│  1 Target                   │  Multiple Targets             │
│  ↓                          │  ↓                            │
│  Scanner                    │  Parallel Scanner             │
│  ↓                          │  ↓                            │
│  JSON Results               │  Aggregated Results            │
│  ↓                          │  ↓                            │
│  AI Analysis                │  AI Analysis                   │
│  ↓                          │  ↓                            │
│  HTML Report                │  HTML Report                   │
│                             │                               │
└─────────────────────────────┴───────────────────────────────┘
```

OmniScan dipisahkan menjadi:

### 🔹 Feature 1 — Single Scan

Digunakan ketika ingin melakukan pemeriksaan terhadap satu target.

### 🔹 Feature 2 — Mass Scan

Digunakan ketika ingin melakukan pemeriksaan terhadap banyak target dari sebuah file.

---

# ✨ Features

## 🔍 Single Target Scan

Single Scan memungkinkan pengguna memasukkan satu URL target.

Contoh:

```bash
python main.py single --url https://example.com
```

Workflow:

```text
Target
  │
  ▼
Scope Validation
  │
  ▼
Passive Scanner
  │
  ▼
Finding Collection
  │
  ▼
JSON Result
  │
  ▼
AI Analyzer
  │
  ▼
HTML Security Report
```

---

# 🚀 Mass Scan

Mass Scan digunakan untuk memproses banyak target sekaligus.

Input:

```text
targets.txt
```

Contoh:

```text
https://example-one.com/
https://example-two.com/
https://example-three.com/
```

Kemudian:

```bash
python main.py mass -i targets.txt
```

OmniScan akan membaca setiap target dari file tersebut.

Secara konseptual:

```text
targets.txt
     │
     ├── Target 01
     ├── Target 02
     ├── Target 03
     ├── Target 04
     └── Target N
             │
             ▼
       Parallel Workers
             │
             ▼
       Scope Validation
             │
             ▼
        Passive Scan
             │
             ▼
      Result Aggregation
             │
             ▼
          AI Layer
             │
             ▼
        HTML Report
```

---

# 🤖 AI-Powered Security Report

Salah satu fitur utama OmniScan adalah **AI-assisted report generation**.

AI tidak digunakan untuk menggantikan scanner.

Scanner tetap menghasilkan data teknis.

AI digunakan untuk membantu:

* memahami finding
* menjelaskan dampak
* mengelompokkan informasi
* membuat ringkasan
* menjelaskan tingkat risiko
* membuat rekomendasi remediation
* menyusun laporan yang lebih mudah dibaca manusia

---

## 🧠 AI Architecture

```text
                 ┌─────────────────┐
                 │     TARGET      │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │  SCOPE CHECK    │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │ PASSIVE SCANNER │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │  JSON FINDINGS  │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │   AI ANALYZER   │
                 └────────┬────────┘
                          │
              ┌───────────┼───────────┐
              ▼           ▼           ▼
          Summary      Impact     Remediation
              │           │           │
              └───────────┼───────────┘
                          ▼
                 ┌─────────────────┐
                 │   HTML REPORT   │
                 └─────────────────┘
```

---

# 🔐 Scope Enforcement

OmniScan memiliki mekanisme scope enforcement.

**Jangan menghapus atau menonaktifkan scope enforcement.**

Tujuannya adalah memastikan scanner hanya bekerja terhadap target yang memang diizinkan.

Konfigurasi contoh:

```json
{
  "allowed_domains": [],
  "allowed_domains_file": "authorized-domains.txt",
  "allow_subdomains": true,
  "explicit_urls": [],
  "excluded_domains": [],
  "excluded_paths": [
    "/logout",
    "/delete",
    "/destroy",
    "/remove"
  ],
  "allowed_schemes": [
    "http",
    "https"
  ],
  "maximum_crawl_depth": 2,
  "maximum_urls_per_target": 150,
  "allowed_scan_modes": [
    "passive"
  ]
}
```

---

# 📁 authorized-domains.txt

File ini digunakan untuk menentukan domain yang diperbolehkan.

Contoh:

```text
example.com
example.org
```

Dengan:

```json
"allow_subdomains": true
```

maka subdomain dari domain yang diizinkan juga dapat termasuk dalam scope sesuai implementasi scope validator.

Contoh:

```text
api.example.com
dev.example.com
staging.example.com
```

**Gunakan hanya domain yang memang berada dalam scope pengujian.**

---

# 📋 targets.txt

Untuk Mass Scan, gunakan file:

```text
targets.txt
```

Contoh:

```text
https://example.com/
https://api.example.com/
https://staging.example.com/
```

Kemudian:

```bash
python main.py mass -i targets.txt
```

---

# 🧪 Command Reference

## 1. Menampilkan bantuan

```bash
python main.py --help
```

Gunakan command ini untuk melihat daftar command yang tersedia pada versi OmniScan yang sedang digunakan.

---

# 2. Single Scan

Format umum:

```bash
python main.py single --url <URL>
```

Contoh:

```bash
python main.py single --url https://example.com/
```

Single Scan cocok untuk:

* debugging scanner
* pengujian satu target
* validasi template
* pemeriksaan hasil scanner
* pengujian AI report

---

# 3. Mass Scan

Format:

```bash
python main.py mass -i targets.txt
```

Contoh:

```bash
python main.py mass -i targets.txt
```

**Catatan penting:**

`-i` / `--targets` adalah file input.

Jangan menggunakan:

```bash
python main.py mass -i https://example.com
```

Karena OmniScan akan menganggap:

```text
https://example.com
```

sebagai nama file.

Akibatnya Windows dapat menghasilkan error seperti:

```text
Targets file not found
```

---

# ❌ Kesalahan Command yang Umum

## Salah

```bash
python main.py mass -i https://example.com/
```

Karena `-i` membutuhkan file.

## Benar

Buat:

```text
targets.txt
```

Isi:

```text
https://example.com/
```

Kemudian:

```bash
python main.py mass -i targets.txt
```

---

# 🧠 AI Configuration

AI sebaiknya dipisahkan dari konfigurasi scanner.

Contoh konsep:

```text
config/
├── scanner.json
├── ai.json
└── scope.json
```

Contoh konfigurasi AI:

```json
{
  "enabled": true,
  "provider": "openai",
  "model": "YOUR_MODEL",
  "temperature": 0.2,
  "max_output_tokens": 4000
}
```

Jangan menyimpan API key langsung di repository.

Gunakan environment variable.

Contoh Windows CMD:

```cmd
set AI_API_KEY=YOUR_API_KEY
```

PowerShell:

```powershell
$env:AI_API_KEY="YOUR_API_KEY"
```

Linux/macOS:

```bash
export AI_API_KEY="YOUR_API_KEY"
```

Kemudian aplikasi mengambil key tersebut dari environment.

---

# 🔒 Jangan Commit API Key

Jangan pernah melakukan:

```text
AI_API_KEY=sk-xxxxxxxxxxxxxxxx
```

ke GitHub.

Gunakan:

```text
.env
```

dan masukkan ke:

```text
.gitignore
```

Contoh:

```gitignore
.env
*.log
reports/
results/
__pycache__/
*.pyc
```

Buat template:

```text
.env.example
```

Contoh:

```env
AI_API_KEY=
AI_MODEL=
AI_PROVIDER=
```

---

# 🤖 Apa yang Dilakukan AI?

AI menerima hasil scanner yang sudah terstruktur.

Misalnya scanner menemukan:

```json
{
  "category": "CORS",
  "severity": "medium",
  "confidence": "high",
  "target": "https://example.com",
  "matched_url": "https://example.com/api"
}
```

AI kemudian dapat mengubahnya menjadi penjelasan seperti:

```text
Finding: CORS Misconfiguration

Severity:
Medium

Confidence:
High

Description:
The endpoint appears to expose a CORS configuration that
should be reviewed.

Potential Impact:
Depending on the response headers and authentication
configuration, an overly permissive CORS policy may allow
untrusted origins to access browser-readable responses.

Recommendation:
Restrict allowed origins to trusted domains and avoid
unnecessary credential sharing.
```

AI **tidak boleh dianggap sebagai bukti final**.

Hasil scanner dan bukti HTTP tetap menjadi sumber teknis utama.

---

# 📊 AI Report Structure

HTML report dapat dibuat dengan struktur:

```text
┌─────────────────────────────────────────┐
│              OMNISCAN REPORT            │
├─────────────────────────────────────────┤
│ Target                                  │
│ Scan Time                               │
│ Scan Mode                               │
│ Scanner Version                         │
├─────────────────────────────────────────┤
│ Executive Summary                       │
├─────────────────────────────────────────┤
│ Severity Overview                       │
│                                         │
│ Critical   █████                         │
│ High       █████████                     │
│ Medium     ███████                       │
│ Low        ███                           │
│ Info       ██                            │
├─────────────────────────────────────────┤
│ Findings                                │
│                                         │
│ [HIGH] Example Finding                  │
│                                         │
│ Description                             │
│ Evidence                                │
│ Impact                                  │
│ Recommendation                          │
│ AI Analysis                             │
└─────────────────────────────────────────┘
```

---

# 📑 Recommended Report Sections

Setiap finding sebaiknya memiliki:

### Finding

Nama finding.

### Category

Kategori keamanan.

Contoh:

```text
CORS
CSRF
Security Headers
Information Disclosure
Authentication
Session
Access Control
```

### Severity

Contoh:

```text
INFO
LOW
MEDIUM
HIGH
CRITICAL
```

### Confidence

Contoh:

```text
LOW
MEDIUM
HIGH
```

### Target

Target yang diperiksa.

### Matched URL

URL yang menghasilkan finding.

### Evidence

Data teknis dari scanner.

### Description

Penjelasan mengenai finding.

### Impact

Potensi dampak keamanan.

### Recommendation

Saran mitigasi.

### AI Analysis

Interpretasi tambahan dari AI.

---

# 🖥️ Recommended Project Structure

Contoh struktur:

```text
OmniScan/
│
├── main.py
│
├── config/
│   ├── scanner.json
│   ├── ai.json
│   └── scope.json
│
├── authorized-domains.txt
├── targets.txt
│
├── scanner/
│   ├── __init__.py
│   ├── passive.py
│   ├── crawler.py
│   └── scope.py
│
├── ai/
│   ├── __init__.py
│   ├── analyzer.py
│   ├── prompts.py
│   └── report.py
│
├── reports/
│
├── results/
│
├── templates/
│
├── logs/
│
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

Struktur aktual dapat berbeda tergantung implementasi.

---

# ⚙️ Installation

Clone repository:

```bash
git clone https://github.com/YOUR_USERNAME/OmniScan.git
```

Masuk ke directory:

```bash
cd OmniScan
```

Buat virtual environment:

### Windows

```cmd
python -m venv .venv
.venv\Scripts\activate
```

### Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# 🧪 Test Installation

Jalankan:

```bash
python main.py --help
```

Jika berhasil, OmniScan akan menampilkan command yang tersedia.

---

# 🎯 Basic Workflow

## Step 1 — Configure Scope

Edit:

```text
authorized-domains.txt
```

Contoh:

```text
example.com
```

---

## Step 2 — Configure Target

Single Scan:

```bash
python main.py single --url https://example.com/
```

Mass Scan:

```text
targets.txt
```

Isi:

```text
https://example.com/
https://api.example.com/
```

Kemudian:

```bash
python main.py mass -i targets.txt
```

---

# 🚦 Passive Mode

OmniScan menggunakan passive scanning sebagai mode default.

Passive scanning berfokus pada observasi dan analisis terhadap informasi yang tersedia dari request/response dan crawling yang diizinkan.

Konfigurasi:

```json
"allowed_scan_modes": [
  "passive"
]
```

Hal ini sengaja dibuat untuk mengurangi risiko request destruktif.

---

# 🛑 Protected Paths

OmniScan dapat mengecualikan path sensitif seperti:

```text
/logout
/delete
/destroy
/remove
```

Contoh:

```json
"excluded_paths": [
  "/logout",
  "/delete",
  "/destroy",
  "/remove"
]
```

Tujuannya adalah mengurangi kemungkinan scanner melakukan request terhadap endpoint yang memiliki efek perubahan atau penghapusan data.

---

# 🧵 Mass Scan Architecture

Mass Scan dapat menggunakan worker/thread pool agar beberapa target dapat diproses secara bersamaan.

Contoh konsep:

```text
                TARGET LIST
                    │
          ┌─────────┴─────────┐
          ▼         ▼         ▼
       Worker 1  Worker 2  Worker 3
          │         │         │
          ▼         ▼         ▼
       Target A  Target B  Target C
          │         │         │
          └─────────┬─────────┘
                    ▼
             Result Collector
                    │
                    ▼
              JSON Aggregator
                    │
                    ▼
                AI Analyzer
                    │
                    ▼
              HTML Generator
```

Keuntungan:

* lebih efisien untuk banyak target
* hasil dapat dikumpulkan terpusat
* setiap target dapat memiliki status terpisah
* error satu target tidak harus menghentikan seluruh proses

---

# 📦 Result Management

Hasil scan sebaiknya dipisahkan berdasarkan run.

Contoh:

```text
results/
└── 2026-09-13_171000/
    ├── summary.json
    ├── target-001.json
    ├── target-002.json
    └── target-003.json
```

Report:

```text
reports/
└── 2026-09-13_171000/
    ├── report.html
    └── ai-report.html
```

Dengan struktur seperti ini, hasil dari beberapa sesi scanning tidak tercampur.

---

# 📈 Example Console Output

Contoh tampilan:

```text
╔══════════════════════════════════════════════╗
║                 OMNISCAN                     ║
║      Passive Web Security Scanner            ║
╚══════════════════════════════════════════════╝

[INFO] Loading configuration...
[INFO] Loading authorized scope...
[INFO] Scope validation enabled.
[INFO] Starting Mass Scan...

[01/05] https://example-one.com
       ├─ Scope       : PASS
       ├─ Crawl       : OK
       ├─ Findings    : 4
       └─ Status      : COMPLETE

[02/05] https://example-two.com
       ├─ Scope       : PASS
       ├─ Crawl       : OK
       ├─ Findings    : 2
       └─ Status      : COMPLETE

[INFO] Scan completed.

[INFO] Generating AI analysis...
[INFO] Generating HTML report...

[SUCCESS] Report generated.
```

---

# 🎨 HTML Report Concept

Report sebaiknya memiliki visual hierarchy.

Contoh:

```text
╔══════════════════════════════════════════════╗
║              OMNISCAN REPORT                 ║
║         Security Assessment                  ║
╠══════════════════════════════════════════════╣
║                                              ║
║  TARGETS            FINDINGS       RISK      ║
║     12                  37          MEDIUM    ║
║                                              ║
╠══════════════════════════════════════════════╣
║               SEVERITY                       ║
║                                              ║
║ Critical  ███                                ║
║ High      ███████                            ║
║ Medium    ███████████                        ║
║ Low       █████                              ║
║ Info      █████████                          ║
╠══════════════════════════════════════════════╣
║              FINDINGS                        ║
║                                              ║
║ [HIGH] Security Finding                     ║
║                                              ║
║ Description                                  ║
║ Evidence                                     ║
║ Impact                                       ║
║ Remediation                                  ║
║ AI Analysis                                  ║
╚══════════════════════════════════════════════╝
```

---

# 🧠 AI Report Philosophy

AI report OmniScan sebaiknya mengikuti prinsip:

```text
RAW DATA
   ↓
TECHNICAL EVIDENCE
   ↓
DETERMINISTIC FINDING
   ↓
AI INTERPRETATION
   ↓
HUMAN REVIEW
```

AI tidak boleh mengubah fakta teknis.

Misalnya scanner menemukan:

```text
status_code = 200
```

AI tidak boleh mengklaim:

```text
The server is definitely vulnerable.
```

tanpa bukti tambahan.

AI sebaiknya mengatakan:

```text
The observed behavior may indicate a configuration
that should be reviewed.
```

Dengan demikian AI berfungsi sebagai **analysis assistant**, bukan sebagai sumber bukti tunggal.

---

# 🔬 Finding Confidence

Confidence dan severity sebaiknya dipisahkan.

Contoh:

```text
Severity  : HIGH
Confidence: LOW
```

Artinya jika finding benar, dampaknya tinggi, tetapi bukti yang tersedia masih lemah.

Sebaliknya:

```text
Severity  : LOW
Confidence: HIGH
```

berarti finding cukup jelas tetapi dampaknya rendah.

---

# 🧩 Error Handling

OmniScan sebaiknya tidak berhenti hanya karena satu target mengalami error.

Contoh:

```text
Target A → SUCCESS
Target B → TIMEOUT
Target C → SUCCESS
Target D → CONNECTION ERROR
Target E → SUCCESS
```

Hasil akhir tetap:

```text
Scan completed:
Successful : 3
Failed     : 2
Total      : 5
```

Error sebaiknya disimpan:

```text
logs/
```

dan bukan menyebabkan seluruh Mass Scan berhenti.

---

# 📝 Logging

Contoh:

```text
2026-09-13 17:08:47 | INFO     | omniscan | Starting scan
2026-09-13 17:08:48 | INFO     | omniscan | Scope validation passed
2026-09-13 17:08:49 | WARNING  | omniscan | Request timeout
2026-09-13 17:08:50 | INFO     | omniscan | Scan completed
```

Level logging:

```text
DEBUG
INFO
WARNING
ERROR
CRITICAL
```

---

# 🛠️ Troubleshooting

## Error: Targets file not found

Jika muncul:

```text
Targets file not found
```

kemungkinan command salah.

Jangan:

```bash
python main.py mass -i https://example.com
```

Gunakan:

```bash
python main.py mass -i targets.txt
```

---

## Error: Mass Scan accepts a target file

Jika muncul:

```text
Mass Scan accepts a target file, not -u/--url
```

kamu sedang menggunakan flag URL pada Mass Scan.

Gunakan:

```bash
python main.py mass -i targets.txt
```

---

# 🧪 Development Testing

Untuk pengembangan, gunakan:

* localhost
* lab environment
* aplikasi vulnerable yang memang disediakan untuk testing
* domain milik sendiri
* target yang secara eksplisit masuk scope

Contoh:

```text
http://127.0.0.1:8000
```

atau environment lab yang memang kamu kendalikan.

---

# ⚠️ Responsible Use

OmniScan dibuat untuk:

* security research
* defensive security
* authorized penetration testing
* bug bounty dalam scope
* laboratory testing
* educational purposes

**Jangan melakukan scanning terhadap sistem yang tidak kamu miliki atau tidak memberikan izin pengujian.**

Selalu periksa:

```text
1. Program scope
2. Authorized domains
3. Allowed testing methods
4. Rate limits
5. Excluded endpoints
6. Rules of engagement
```

Scope enforcement OmniScan **jangan dihapus hanya untuk mempermudah scanning**.

---

# 🔐 Security Best Practices

Sebelum menjalankan OmniScan:

### ✔ Pastikan target authorized

```text
authorized-domains.txt
```

### ✔ Gunakan passive mode terlebih dahulu

```json
"allowed_scan_modes": ["passive"]
```

### ✔ Jangan commit API key

Gunakan:

```text
.env
```

### ✔ Jangan commit hasil sensitif

Gunakan:

```text
.gitignore
```

### ✔ Review AI output

AI dapat melakukan interpretasi yang tidak sempurna.

---

# 📊 Recommended GitHub Screenshots

Agar repository terlihat lebih profesional, tambahkan screenshot seperti:

```text
docs/
├── banner.png
├── terminal-single.png
├── terminal-mass.png
├── ai-analysis.png
├── html-dashboard.png
├── finding-detail.png
└── architecture.png
```

README kemudian dapat menampilkan:

```markdown
<p align="center">
  <img src="docs/banner.png" width="900">
</p>
```

---

# 🎬 Demo Section

Tambahkan GIF terminal:

```markdown
<p align="center">
  <img src="docs/demo.gif" width="900">
</p>
```

Contoh workflow GIF:

```text
START
  ↓
Load Scope
  ↓
Load Targets
  ↓
Scan
  ↓
Findings
  ↓
AI Analysis
  ↓
HTML Report
```

GIF seperti ini membuat README jauh lebih hidup dibanding hanya kumpulan teks.

---

# 🌌 Architecture Visualization

Tambahkan diagram:

```text
                     ┌──────────────────────┐
                     │       USER           │
                     └──────────┬───────────┘
                                │
                 ┌──────────────┴──────────────┐
                 │                             │
                 ▼                             ▼
        ┌─────────────────┐          ┌─────────────────┐
        │   SINGLE SCAN   │          │    MASS SCAN    │
        └────────┬────────┘          └────────┬────────┘
                 │                            │
                 └────────────┬───────────────┘
                              ▼
                    ┌──────────────────┐
                    │ SCOPE VALIDATOR  │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ PASSIVE SCANNER  │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ RESULT COLLECTOR │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │   AI ANALYZER    │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │  HTML GENERATOR  │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ SECURITY REPORT  │
                    └──────────────────┘
```

---

# 🏆 Why OmniScan?

OmniScan mencoba menggabungkan:

```text
Simple CLI
     +
Multi Target
     +
Parallel Processing
     +
Scope Enforcement
     +
Passive Security Checks
     +
Structured Results
     +
AI Analysis
     +
HTML Reporting
```

Tujuannya bukan sekadar melakukan scanning.

Tujuannya adalah membuat workflow:

```text
SCAN → UNDERSTAND → DOCUMENT
```

lebih cepat dan terstruktur.

---

# 📚 Roadmap

## v1

* [x] Single Scan
* [x] Mass Scan
* [x] Scope Enforcement
* [x] Passive Scanning
* [x] JSON Results
* [x] HTML Report
* [x] AI Analysis

## Future

* [ ] Better dashboard
* [ ] Finding deduplication
* [ ] Historical scan comparison
* [ ] Export PDF
* [ ] Improved AI summaries
* [ ] Custom report templates
* [ ] Plugin architecture
* [ ] Better crawler controls
* [ ] Scan scheduling
* [ ] More structured finding metadata
* [ ] CI/CD integration

---

# ⭐ Contributing

Pull requests are welcome.

Before submitting changes:

```bash
git pull
```

Test your changes locally.

Kemudian:

```bash
git add .
git commit -m "Improve scanner"
git push
```

Untuk perubahan besar, buat issue terlebih dahulu agar desain perubahan dapat didiskusikan.

---

# 📜 License

Tambahkan license sesuai kebutuhan project.

Contoh:

```text
MIT License
```

atau gunakan license lain sesuai kebutuhan project.

---

# 👨‍💻 Author

**M. Hedy Wibianto**

Security Researcher • Developer • Cybersecurity Learner

Project focus:

```text
Web Security
Security Automation
Python
AI-assisted Analysis
Security Reporting
```

---

# ⭐ Support

Jika project ini membantu proses learning atau security research kamu:

⭐ Star repository
🍴 Fork repository
🐛 Report bugs
💡 Suggest improvements
🤝 Contribute

---

<p align="center">

### 🛡️ OmniScan

**Scan responsibly. Analyze carefully. Report clearly.**

</p>
