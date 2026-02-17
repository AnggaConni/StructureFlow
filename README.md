# StructureFlow

Rangkuman Checklist (Penting!)

Agar tidak error, pastikan 3 hal ini terhubung dengan ID yang sama:

DUMMY_DATA: const DUMMY_DATA = { laporan_kegiatan: { ... } }

GUIDANCE: const GUIDANCE = { laporan_kegiatan: { ... } }

REGISTRY: const MODULE_REGISTRY_DEFINITION = [ { id: 'laporan_kegiatan', ... } ]

Jika ID berbeda (misal: laporan_kegiatan vs laporankegiatan), aplikasi mungkin akan blank atau error saat template dipilih.

Panduan Modifikasi StructureFlow (Edisi Angga C.S.)

Dokumen ini menjelaskan cara menambahkan Template Dokumen Baru ke dalam aplikasi StructureFlow.

Sistem ini bersifat modular. Untuk menambahkan satu jenis dokumen baru (misalnya: "Proposal Bisnis"), Anda perlu menyunting 3 bagian di dalam file StructureFlow v3.5 - Angga Edition.html.

Pastikan Anda menggunakan Text Editor (seperti VS Code, Notepad++, atau Sublime Text).

Langkah 1: Tambah Dummy Data (Konten Contoh)

Cari variabel const DUMMY_DATA di dalam kode. Ini berisi konten bahasa Inggris yang akan muncul ketika pengguna memilih tombol "Load Example".

Format:

nama_id_unik: {
  title: 'Judul Dokumen Contoh',
  sections: [
    { key: 'nama_bagian_1', content: '<h3>Judul Bagian</h3><p>Isi contoh...</p>' },
    { key: 'nama_bagian_2', content: '<h3>Judul Bagian</h3><p>Isi contoh...</p>' }
  ]
},



Tips: - Gunakan nama_id_unik yang konsisten (huruf kecil, tanpa spasi, pakai underscore). Contoh: project_proposal.

Isi content boleh mengandung HTML standar (<h3>, <p>, <ul>, <li>).

Langkah 2: Tambah Guidelines (Panduan Bilingual)

Cari variabel const GUIDANCE. Ini mengontrol teks bantuan di panel kanan (Guidance Engine). Anda harus menyediakan versi EN (Inggris) dan ID (Indonesia).

Format:

nama_id_unik: { // Harus SAMA dengan ID di Langkah 1
  
  // Analogi (muncul di atas panel panduan)
  _analogy: { 
    en: 'Analogy in English.', 
    id: 'Analogi dalam Bahasa Indonesia.' 
  },

  // Panduan per bagian (kunci harus sama dengan 'key' di Langkah 1)
  nama_bagian_1: {
    en: { 
      what: 'What to write here?', 
      tip: 'A short tip.' 
    },
    id: { 
      what: 'Apa yang harus ditulis di sini?', 
      tip: 'Tips singkat.' 
    }
  },
  
  // Ulangi untuk bagian lainnya...
},



Langkah 3: Daftarkan Tombol (Module Registry)

Cari variabel const MODULE_REGISTRY_DEFINITION. Ini adalah daftar yang memunculkan tombol di halaman depan (Landing Page).

Format:

{
  id: 'nama_id_unik', // WAJIB SAMA persis dengan Langkah 1 & 2
  name: 'Nama Yang Muncul di Tombol',
  category: 'academic', // Pilihan: 'academic', 'policy', atau 'media'
  schema_version: '3.0.0', // Biarkan tetap ini
  
  // Urutan bagian yang akan dibuat (harus cocok dengan 'key' di Langkah 1 & 2)
  structural_sections: ['nama_bagian_1', 'nama_bagian_2', 'nama_bagian_3'],
  
  color: 'blue', // Pilihan warna: 'blue', 'emerald', 'orange'
  description: 'Deskripsi singkat yang muncul di bawah tombol.'
},

