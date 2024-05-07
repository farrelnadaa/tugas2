<template>
  <div id="app">
    <h1 :style="{ color: primaryColor }">Daftar Kegiatan</h1>
    <input type="text" v-model="message" placeholder="Ketik pesan di sini..." @keydown.enter="handleSubmit">
    <button @click="toggleColor">perbesar</button> <!-- Tombol untuk mengubah dan mengembalikan warna -->
    <button @click="toggleHighlight">ubah warna</button> <!-- Mengubah nama tombol -->
    <p :class="{ 'text-danger': hasError }" :style="{ fontSize: fontSize + 'px' }">
      {{ message }}
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: '',
      primaryColor: 'black',
      hasError: false,
      fontSize: 18,
      originalColor: 'black', // Menyimpan warna asli
      originalFontSize: 16, // Menyimpan ukuran font asli
      colorChanged: false // Menyimpan status apakah warna sudah diubah atau belum
    };
  },
  methods: {
    toggleColor() {
      if (this.colorChanged) {
        this.resetColor(); // Mengembalikan warna jika warna sudah diubah sebelumnya
      } else {
        this.changeColor(); // Mengubah warna jika warna belum diubah sebelumnya
      }
      this.colorChanged = !this.colorChanged; // Toggle status warna
    },
    changeColor() {
      this.hasError = true;
      this.fontSize = 24;
    },
    toggleHighlight() { // Mengubah nama method
      this.hasError = !this.hasError; // Mengganti nilai hasError menjadi kebalikan nilai sebelumnya
    },
    resetColor() {
      this.primaryColor = this.originalColor;
      this.hasError = false;
      this.fontSize = this.originalFontSize;
    },
    handleSubmit() {
      // Tambahkan logika untuk meng-handle input teks saat tombol "Enter" ditekan
      console.log('Enter pressed!');
      // Misalnya, Anda bisa memanggil method yang ingin dijalankan saat tombol "Enter" ditekan
      // this.changeColor();
    }
  }
};
</script>

<style scoped>
  body {
      background-image: url('https://wallpapers.com/images/featured/aesthetic-laptop-jtemra7do9fhwkgf.jpg'); /* Ganti URL dengan URL gambar yang ingin Anda gunakan */
      background-size: cover;
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    #app {
      text-align: center;
      background-color: rgba(255, 255, 255, 0.8);
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    .text-danger {
      color: rgb(245, 8, 0);
    }
    h1 {
      color: #2c3e50;
      font-size: 24px;
      margin-bottom: 20px;
    }
    button {
      padding: 10px 20px;
      margin: 0 5px;
      background-color: #676b6e;
      border: none;
      color: #fff;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #471f03;
    }
    p {
      font-size: 18px;
      margin-top: 20px;
    }
    input[type="text"] {
      width: 200px;
      padding: 10px;
      margin-bottom: 10px;
      border: 1px solid #ccc;
      border-radius: 3px; /* Mengubah border-radius menjadi lebih kecil */
    }
</style>
