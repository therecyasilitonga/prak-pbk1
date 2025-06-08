<template>
  <div class="container">
    <h1>Booking Make-Up</h1>

    <div class="form">
      <input v-model="name" placeholder="Nama Customer" />
      <select v-model="selectedService">
        <option disabled value="">Pilih Layanan</option>
        <option v-for="(service, index) in services" :key="index" :value="service.title">
          {{ service.title }}
        </option>
      </select>
      <button @click="book">Booking</button>
    </div>

    <p v-if="bookings.length === 0">Belum ada booking yang masuk.</p>
    <ul v-else>
      <li v-for="(booking, index) in bookings" :key="index">
        {{ booking.name }} memesan layanan {{ booking.service }}
      </li>
    </ul>

    <h2>Layanan MUA</h2>
    <div class="cards">
      <div v-for="(service, index) in services" :key="index" class="card">
        <img :src="service.img" :alt="service.title" />
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
          img: '/images/wedding.jpg',
          description: 'Make-up untuk acara pernikahan',
        },
        {
          title: 'Photoshoot Make-up',
          img: '/images/photoshoot.jpg',
          description: 'Make-up untuk sesi foto profesional',
        },
        {
          title: 'Therecya Silitonga',
          img: '/images/theresya.jpg',
          description: '233510300',
        },
      ],
    };
  },
  methods: {
    book() {
      if (this.name && this.selectedService) {
        this.bookings.push({ name: this.name, service: this.selectedService });
        this.name = '';
        this.selectedService = '';
      } else {
        alert('Lengkapi form terlebih dahulu.');
      }
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 800px;
  margin: auto;
  padding: 2rem;
  color: white;
  text-align: center;
  background-color: #121212;
}
.form {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 1rem;
}
input, select {
  padding: 0.5rem;
}
button {
  padding: 0.5rem 1rem;
  background-color: black;
  color: white;
  border: none;
  cursor: pointer;
}
.cards {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
  margin-top: 2rem;
}
.card {
  background: #1e1e1e;
  padding: 1rem;
  border: 1px solid #444;
  border-radius: 10px;
  width: 200px;
}
.card img {
  width: 100%;
  height: auto;
  border-radius: 5px;
}
</style>
