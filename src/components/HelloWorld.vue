<script setup>
import { ref } from 'vue'

const name = ref('')
const serviceType = ref('Wedding')
const submitted = ref(false)

const count = ref(0)

function submitForm() {
  submitted.value = true
}
</script>

<template>
  <!-- Declarative Rendering -->
  <h1>Pendaftaran Make-Up Artist</h1>

  <!-- Form Bindings -->
  <form @submit.prevent="submitForm">
    <label>Nama:</label>
    <input type="text" v-model="name" placeholder="Masukkan nama Anda" />

    <label>Jenis Layanan:</label>
    <select v-model="serviceType">
      <option>Wedding</option>
      <option>Photoshoot</option>
      <option>Graduation</option>
    </select>

    <!-- Event Listener -->
    <button type="submit">Kirim</button>
  </form>

  <!-- Conditional Rendering -->
  <div v-if="submitted">
    <h2>Data Pendaftaran:</h2>
    <p>Nama: {{ name }}</p>
    <p>Layanan: {{ serviceType }}</p>
    <p>Status: ✅ Terkonfirmasi</p>
  </div>

  <!-- Attribute Binding -->
  <img :src="serviceType === 'Wedding' ? 'wedding.jpg' : 'default.jpg'" alt="Jenis layanan" width="150" />

  <!-- Counter Event Listener -->
  <div class="card">
    <button @click="count++">Klik saya ({{ count }})</button>
  </div>

  <!-- Biodata MUA -->
  <p>BIODATA MUA:</p>
  <p>NAMA: THERECYA SILITONGA</p>
  <p>NPM: 233510300</p>
  <p>KELAS: 4D</p>
</template>

<style scoped>
form {
  margin-bottom: 1rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.card {
  margin-top: 1rem;
}
</style>
