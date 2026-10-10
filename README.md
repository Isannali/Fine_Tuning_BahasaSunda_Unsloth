# Fine-Tuning LLM untuk Bahasa Sunda

Proyek ini bertujuan mengadaptasi Large Language Model (LLM) agar dapat memahami instruksi dan menghasilkan respons dalam bahasa Sunda melalui teknik *Supervised Fine-Tuning* (SFT) menggunakan LoRA dan Unsloth.

## Gambaran Proyek

Model dasar yang digunakan adalah **Qwen3-1.7B-Base**, yang diadaptasi menggunakan dataset instruksi bahasa Sunda. Proses pelatihan menggunakan LoRA untuk memperbarui sebagian kecil parameter model sehingga kebutuhan komputasi dan memori lebih efisien.

Proyek ini mencakup tahapan persiapan dataset, konfigurasi model, fine-tuning, pengujian inferensi, dan penyimpanan model hasil pelatihan.

## Teknologi yang Digunakan

- **Bahasa pemrograman:** Python
- **Model dasar:** Qwen3-1.7B-Base
- **Fine-tuning:** LoRA, PEFT, Supervised Fine-Tuning (SFT)
- **Framework:** Unsloth, PyTorch, Hugging Face Transformers, TRL
- **Dataset:** [Alpaca Sundanese 10K](https://huggingface.co/datasets/rmdhirr/alpaca-sundanese-10k)
- **Lingkungan pengembangan:** Google Colab

## Metodologi

1. **Persiapan model:** Memuat Qwen3-1.7B-Base dengan konfigurasi kuantisasi 4-bit untuk mengurangi penggunaan memori.
2. **Konfigurasi LoRA:** Menerapkan LoRA pada modul proyeksi perhatian dan feed-forward model dengan rank 16.
3. **Pemrosesan dataset:** Mengubah data instruksi, input, dan output menjadi format prompt terstruktur menggunakan template Alpaca.
4. **Fine-tuning:** Melatih model menggunakan SFTTrainer dengan konfigurasi batch size 2, gradient accumulation 4, learning rate 0,0002, dan 300 langkah pelatihan.
5. **Pengujian inferensi:** Menguji model dengan pertanyaan berbahasa Sunda dan menghasilkan respons menggunakan model yang telah diadaptasi.
6. **Penyimpanan model:** Menyimpan bobot adapter LoRA dan tokenizer untuk penggunaan selanjutnya.

## Contoh Inferensi

Contoh instruksi yang digunakan untuk menguji model:

**Pertanyaan:**
> Contohken Bilangan Fibonacci teh jiga kumaha?

Model kemudian diminta menghasilkan respons dalam bahasa Sunda. Hasil aktual dapat dilihat dengan menjalankan sel inferensi pada notebook.

## Cara Menjalankan

1. Buka notebook `Fine_Tuning_Bahasa_sunda_unsloth.ipynb` menggunakan Google Colab.
2. Siapkan lingkungan dan instal dependensi yang diperlukan.
3. Jalankan sel notebook secara berurutan untuk memuat model, memproses dataset, dan melakukan fine-tuning.
4. Jalankan sel inferensi untuk menguji respons model.
5. Simpan model hasil pelatihan dan tokenizer ke Google Drive.

Notebook menggunakan Google Drive untuk menyimpan hasil pelatihan. Pastikan Google Drive telah terhubung dan direktori penyimpanan tersedia.

## Hasil dan Pengembangan Lanjutan

Proyek ini menerapkan alur fine-tuning LLM menggunakan pendekatan parameter-efficient fine-tuning (PEFT). Evaluasi kualitas respons, perbandingan dengan model dasar, dan pengukuran metrik kuantitatif dapat ditambahkan untuk menilai peningkatan kemampuan model dalam memahami dan menghasilkan bahasa Sunda.

## Catatan

Konfigurasi 300 langkah pelatihan digunakan sebagai eksperimen awal. Hasil akhir bergantung pada dataset, konfigurasi pelatihan, dan lingkungan komputasi yang digunakan.