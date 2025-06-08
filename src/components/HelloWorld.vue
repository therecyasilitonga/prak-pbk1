<template>
  <div class="container">
    <h1>Booking Make-up</h1>

    <!-- Form Bindings -->
    <form @submit.prevent="submitBooking">
      <input v-model="name" type="text" placeholder="Nama Customer" required />
      <select v-model="selectedService" required>
        <option disabled value="">Pilih Layanan</option>
        <option v-for="(service, i) in services" :key="i">{{ service.title }}</option>
      </select>
      <button type="submit">Booking</button>
    </form>

    <!-- Conditional Rendering -->
    <p v-if="bookings.length === 0">Belum ada booking yang masuk.</p>

    <!-- Declarative Rendering -->
    <ul v-else>
      <li v-for="(b, i) in bookings" :key="i">
        {{ b.name }} memesan layanan <strong>{{ b.service }}</strong>
      </li>
    </ul>

    <h2>Layanan MUA</h2>
    <div class="gallery">
      <div class="card" v-for="(service, i) in services" :key="i">
        <!-- Attribute Bindings -->
        <img :src="service.img" :alt="service.title" @click="showAlert(service)" />
        <h3>{{ service.title }}</h3>
        <p>{{ service.description }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      selectedService: '',
      bookings: [],
      services: [
        {
          title: 'Wedding Make-up',
          img: '/src/assets/wedding.jpg',
          description: 'Make-up untuk acara pernikahan'
        },
        {
          title: 'Photoshoot Make-up',
          img: '/src/assets/photoshoot.jpg',
          description: 'Make-up untuk sesi foto profesional'
        },
        {
          title: 'Therecya Silitonga',
          img: '/src/assets/theresya.jpg',
          description: '233510300'
        }
      ]
    }
  },
  methods: {
    submitBooking() {
      this.bookings.push({
        name: this.name,
        service: this.selectedService
      })
      this.name = ''
      this.selectedService = ''
    },
    showAlert(service) {
      alert(`Detail Layanan: ${service.title}\n${service.description}`)
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 800px;
  margin: auto;
  padding: 20px;
  text-align: center;
}

form {
  margin-bottom: 20px;
}

input, select {
  padding: 8px;
  margin: 5px;
  width: 200px;
}

button {
  padding: 8px 16px;
}

.gallery {
  display: flex;
  gap: 15px;
  flex-wrap: wrap;
  justify-content: center;
}

.card {
  border: 1px solid #ccc;
  padding: 10px;
  width: 220px;
}

.card img {
  width: 100%;
  height: auto;
  cursor: pointer;
}
</style>
