# Apa itu StructureFlow? 

StructureFlow adalah alat bantu penulisan cerdas berbasis web yang dirancang untuk membantu Anda menyusun dokumen kompleks—seperti Jurnal Akademis, Proposal Proyek, atau Laporan Riset—dengan struktur yang presisi dan bantuan AI.

Berbeda dengan editor teks biasa yang memberikan Anda "halaman kosong", StructureFlow memberikan Anda kerangka kerja (framework).

🌟 Mengapa Menggunakan StructureFlow?

Menulis dokumen formal seringkali sulit bukan karena kita tidak tahu apa yang ingin ditulis, tetapi karena kita bingung bagaimana menyusunnya.

StructureFlow memecahkan masalah tersebut dengan pendekatan:

Struktur Dulu, Konten Kemudian: Aplikasi ini memecah dokumen besar menjadi bagian-bagian kecil (misal: Abstrak, Pendahuluan, Metodologi).

Panduan Terintegrasi: Setiap bagian dilengkapi instruksi tentang apa yang harus ditulis, sehingga Anda tidak pernah merasa tersesat.

Kecerdasan Buatan (AI): Terhubung langsung dengan Google Gemini untuk membantu Anda membuat draf awal atau memperbaiki kalimat.

🚀 Fitur Unggulan (Edisi v3.5)

Versi khusus ini telah disesuaikan untuk kebutuhan Bapak Angga Conni Saputra dengan fitur-fitur berikut:

1. 🧠 AI Bridge yang Tangguh

Sistem ini menggunakan kecerdasan buatan Google Gemini. Jika satu model AI sedang sibuk atau gangguan, sistem otomatis beralih ke model cadangan (Fallback Mechanism) agar pekerjaan Anda tidak terhenti.

2. 🇮🇩🇺🇸 Panduan & AI Bilingual

Satu-satunya editor yang paham konteks Bahasa Indonesia dan Inggris.

Guidance Engine: Memberikan tips penulisan (seperti "Apa yang harus ditulis di bagian ini?") dalam bahasa pilihan Anda.

Auto-Drafting: Cukup tekan tombol, dan AI akan menulis draf awal untuk Anda dalam Bahasa Indonesia atau Inggris sesuai pengaturan tombol (Toggle ID/EN).

3. 🔒 Privasi Terjamin (Client-Side)

Aplikasi ini berjalan 100% di browser Anda.

Tidak ada database server.

Data Anda tidak disimpan di server pihak ketiga (kecuali dikirim ke Google saat meminta bantuan AI).

Anda memegang kendali penuh atas API Key Anda.

4. 📂 Template Siap Pakai

Tersedia berbagai template standar industri:

Jurnal Akademis: Standar IMRaD (Introduction, Method, Result, Discussion).

Proposal Proyek: Struktur standar untuk pengajuan dana/proyek.

Laporan Riset & Makalah Konferensi.

🛠️ Cara Kerja

Buka Aplikasi: Cukup buka file .html di browser (Chrome/Edge). Tidak perlu instalasi software berat.

Masukkan Kunci: Input Google Gemini API Key Anda (gratis dari Google).

Pilih Template: Pilih jenis dokumen yang ingin dibuat.

Tulis & Kolaborasi dengan AI: Isi setiap bagian. Jika buntu, minta AI untuk menuliskan draf atau memperbaiki tata bahasa.

Ekspor: Setelah selesai, unduh dokumen dalam format Microsoft Word (.doc) yang rapi dan siap diedit lebih lanjut.

🎯 Siapa yang Cocok Menggunakan Ini?

Akademisi & Mahasiswa: Untuk menyusun skripsi, tesis, atau jurnal internasional tanpa pusing memikirkan struktur.

Profesional: Untuk membuat proposal bisnis atau laporan proyek yang terstruktur dan meyakinkan.

Penulis Teknis: Untuk menjaga konsistensi format dalam dokumen panjang.

Dikonsep oleh Tim StructureFlow, dikustomisasi khusus untuk produktivitas Angga Conni Saputra.

# StructureFlow – Custom Template Guide

---

## 🔎 Important Checklist (Read This First!)

To prevent errors or blank screens, make sure these **three parts use the exact same ID**:

```js
// 1️⃣ DUMMY DATA
const DUMMY_DATA = {
  laporan_kegiatan: { ... }
};

// 2️⃣ GUIDANCE
const GUIDANCE = {
  laporan_kegiatan: { ... }
};

// 3️⃣ MODULE REGISTRY
const MODULE_REGISTRY_DEFINITION = [
  { id: 'laporan_kegiatan', ... }
];
```

⚠️ If the IDs are different (for example: `laporan_kegiatan` vs `laporankegiatan`),  
the application may fail to load or display a blank screen when the template is selected.

**The ID must match exactly in all three places.**

---

# How to Add a New Document Template

This document explains how to add a **new document template** (e.g., "Business Proposal") to the StructureFlow application.

The system is modular.  
To add a new document type, you must edit **three sections** inside:

```
StructureFlow v3.5 - Angga Edition.html
```

Use a proper text editor such as:
- VS Code
- Notepad++
- Sublime Text

---

# Step 1 — Add Dummy Data (Example Content)

Locate:

```js
const DUMMY_DATA = { ... };
```

This object contains the example English content shown when the user clicks **"Load Example."**

### Format

```js
unique_id: {
  title: 'Example Document Title',
  sections: [
    {
      key: 'section_one',
      content: '<h3>Section Title</h3><p>Example content...</p>'
    },
    {
      key: 'section_two',
      content: '<h3>Section Title</h3><p>Example content...</p>'
    }
  ]
},
```

### Tips

- Use a consistent `unique_id`
- Lowercase only
- No spaces
- Use underscores  
  Example: `project_proposal`

- The `content` field supports standard HTML:
  - `<h3>`
  - `<p>`
  - `<ul>`
  - `<li>`

---

# Step 2 — Add Bilingual Guidance (Guidance Engine)

Locate:

```js
const GUIDANCE = { ... };
```

This controls the helper text displayed in the right-side panel (Guidance Engine).

You must provide both:
- `en` → English
- `id` → Indonesian

The ID here must be **identical** to Step 1.

### Format

```js
unique_id: { // MUST match the ID in Step 1

  // Analogy (displayed at the top of the guidance panel)
  _analogy: {
    en: 'Analogy in English.',
    id: 'Analogi dalam Bahasa Indonesia.'
  },

  // Section guidance (keys must match Step 1 section keys)
  section_one: {
    en: {
      what: 'What should be written here?',
      tip: 'A short practical tip.'
    },
    id: {
      what: 'Apa yang harus ditulis di sini?',
      tip: 'Tips singkat.'
    }
  },

  // Repeat for additional sections...
},
```

### Important Rules

- `unique_id` must match Step 1.
- Section keys must match the `key` values inside `DUMMY_DATA.sections`.
- Always provide both language versions.

---

# Step 3 — Register the Template (Module Registry)

Locate:

```js
const MODULE_REGISTRY_DEFINITION = [ ... ];
```

This array generates the buttons shown on the landing page.

### Format

```js
{
  id: 'unique_id', // MUST match Steps 1 & 2 exactly
  name: 'Button Display Name',
  category: 'academic', // Options: 'academic', 'policy', 'media'
  schema_version: '3.0.0', // Leave unchanged

  // Must match section keys defined earlier
  structural_sections: [
    'section_one',
    'section_two',
    'section_three'
  ],

  color: 'blue', // Options: 'blue', 'emerald', 'orange'
  description: 'Short description displayed under the button.'
},
```

---

# 🧠 How the System Connects

```
MODULE_REGISTRY_DEFINITION
        ↓
Loads ID
        ↓
DUMMY_DATA (Example Content)
        ↓
GUIDANCE (Helper Text)
```

If one part is missing or mismatched, the template will not render correctly.

---

# ✅ Final Validation Checklist

- [ ] ID matches in all three locations  
- [ ] Section keys are consistent  
- [ ] Both EN and ID guidance exist  
- [ ] No missing commas in objects  
- [ ] `schema_version` remains `'3.0.0'`

---

If everything matches, your new template will appear automatically on the landing page and function correctly.

Happy building 🚀
