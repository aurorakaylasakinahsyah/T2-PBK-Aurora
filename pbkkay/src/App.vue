<template>
  <div class="concert-container">
    <!-- Judul -->
    <h1 class="concert-title">{{ title }}</h1>

    <!-- Deskripsi -->
    <p class="concert-description">{{ description }}</p>

    <!-- Daftar tiket konser -->
    <h2 class="ticket-heading">Pilihan Tiket Konser:</h2>
    <ul class="ticket-list">
      <li v-for="ticket in tickets" :key="ticket.id" @click="selectTicket(ticket)" :class="{ 'selected': ticket === selectedTicket }">
        <div class="ticket-info">
          <span class="ticket-name">{{ ticket.name }}</span>
          <span class="ticket-price">{{ ticket.price }}</span>
        </div>
      </li>
    </ul>

    <!-- Pesan konfirmasi -->
    <transition name="fade">
      <div v-if="selectedTicket" class="confirmation">
        <p>Kamu memilih:</p>
        <div class="selected-ticket">
          <span class="ticket-name">{{ selectedTicket.name }}</span>
          <span class="ticket-price">{{ selectedTicket.price }}</span>
        </div>
        <p>Hay Swiftie!</p>
        <br>
        <button @click="resetSelection">Reset Pilihan</button>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: ' Taylor swift in Jakarta!',
      description: 'Silakan pilih tiket konser favoritmu dari daftar berikut:',
      tickets: [
        { id: 1, name: 'VIP ', price: 'Rp.6.000.000' },
        { id: 2, name: 'Gold ', price: 'Rp.4.000.000' },
        { id: 3, name: 'Silver ', price: 'Rp.2.400.000' },
        { id: 4, name: 'Bronze ', price: 'Rp.1.340.000' }
      ],
      selectedTicket: null
    };
  },
  methods: {
    selectTicket(ticket) {
      this.selectedTicket = ticket;
    },
    resetSelection() {
      this.selectedTicket = null;
    }
  }
};
</script>

<style scoped>
/* Style untuk halaman web */
.concert-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  border-radius: 10px;
  background-color: #f7f7f7;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.concert-title {
  color:rgb(232, 94, 8)0; /* Warna oranye */
  font-size: 32px;
  text-align: center;
}

.concert-description {
  font-size: 18px;
  text-align: center;
}

.ticket-heading {
  margin-top: 20px;
  font-size: 24px;
}

.ticket-list {
  list-style-type: none;
  padding: 0;
}

.ticket-info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.ticket-info:hover {
  background-color: #c14f67;
}

.ticket-name {
  font-size: 18px;
}

.ticket-price {
  font-size: 16px;
}

.selected {
  font-weight: bold;
}

.confirmation {
  margin-top: 20px;
  text-align: center;
}

.selected-ticket {
  margin-bottom: 10px;
}

button {
  background-color: #22bbc9; /* Warna oranye */
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #105887; /* Warna oranye tua */
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
