<template>
  <div>
    <!-- Header-Bereich -->
    <header :dir="direction">
      <h1>CoU</h1>
      <div>
        <input placeholder="Suche" />
      </div>
      <div>
        <!-- Dropdown-Button -->
        <button @click="toggleDropdown">
          <img src="https://cdn-icons-png.flaticon.com/128/7216/7216128.png" alt="menu" />
        </button>
      </div>
    </header>

    <!-- Dropdown-Menü -->
    <ul v-if="dropdownVisible" class="dropdown">
      <li><a href="https://example.com/link1" target="_blank">Unsere KPIs</a></li>
      <li><a href="https://example.com/link2" target="_blank">Co2-Im Überblick</a></li>
      <li><a href="https://example.com/link3" target="_blank">Aktuelles</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Header", // Name der Komponente
  data() {
    return {
      dropdownVisible: false, // Dropdown ist initial ausgeblendet
    };
  },
  methods: {
    toggleDropdown() {
      this.dropdownVisible = !this.dropdownVisible; // Dropdown ein- oder ausblenden
    },
  },
};
</script>

<style scoped>
/* Body-Grundstruktur */
body {
  margin: 0;
  padding: 0;
  height: 100%;
  display: flex;
  flex-direction: column;
}

/* Header-Stil */
header {
  background-color: rgb(72, 141, 86);
  height: 120px;
  padding: 16px;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  box-sizing: border-box;
}

/* Suchfeld */
input {
  border: 0;
  border-radius: 8px;
  width: 200px;
  height: 50px;
  display: flex;
  align-items: center;
}

/* Button-Stil */
button {
  border: 0;
  width: 40px; /* Feste Breite */
  height: 40px; /* Feste Höhe */
  border-radius: 8px;
  align-content: flex-end;
}

/* Überschrift */
h1 {
  font-weight: bold;
  font-size: 55px;
  color: hwb(0 100% 0%);
}

/* Dropdown-Menü */
.dropdown {
  position: absolute;
  top: 140px; /* Unterhalb des Headers */
  right: 16px; /* Am rechten Rand */
  background: white;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  list-style: none;
  padding: 10px;
  margin: 0;
  z-index: 1000; /* Wichtig: Hier wird sichergestellt, dass das Dropdown immer über anderen Elementen liegt */
}

/* Dropdown-Links */
.dropdown li {
  margin: 5px 0;
}

.dropdown a {
  text-decoration: none;
  color: #007BFF;
  font-size: 16px;
}

.dropdown a:hover {
  text-decoration: underline;
}

/* Wenn das Dropdown von Rechts nach Links angezeigt wird */
ul[dir="rtl"] {
  flex-direction: row-reverse; /* Macht die Reihenfolge umgekehrt */
}
</style>
