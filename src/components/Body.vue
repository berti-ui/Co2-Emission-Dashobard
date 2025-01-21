<template>
  <div>
    <div class="body-container">
      <h1>Transparenz für eine nachhaltige Zukunft</h1>
      <h2>
        Wir setzen uns dafür ein, den Klimawandel zu bekämpfen, indem wir Klarheit schaffen:
        Welche Länder und Unternehmen tragen wie viel zu den globalen CO₂-Emissionen bei? Unsere Plattform macht diese Daten sichtbar und zugänglich –
        für mehr Bewusstsein, Verantwortung und Veränderung.
      </h2>

      <!-- Tabelle für CO₂-Emissionsdaten -->
      <div class="table-container">
        <div class="filter">
          <input v-model="filter.land" placeholder="Nach Land filtern" />
          <input v-model="filter.firma" placeholder="Nach Firma filtern" />
        </div>

        <table>
          <thead>
            <tr>
              <th @click="datenSortieren('land')" :class="{ active: sortierschluessel === 'land' }">Land</th>
              <th @click="datenSortieren('firma')" :class="{ active: sortierschluessel === 'firma' }">Firma</th>
              <th @click="datenSortieren('anteil')" :class="{ active: sortierschluessel === 'anteil' }">Anteil an den globalen Emissionen (%)</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="eintrag in paginierteDaten" :key="eintrag.rank">
              <td>{{ eintrag.land }}</td>
              <td>{{ eintrag.firma }}</td>
              <td>{{ eintrag.anteil }}</td>
            </tr>
          </tbody>
        </table>

        <!-- Pagination Controls -->
        <div class="pagination">
          <button @click="changePage(-1)" :disabled="currentPage === 1">Vorherige</button>
          <button @click="changePage(1)" :disabled="currentPage >= totalPages">Nächste</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script scoped>
import countries from '@/assets/countries.json'; // JSON-Datei importieren

export default {
  name: 'Body',
  data() {
    return {
      emissionsDaten: countries, // Daten aus der JSON-Datei verwenden
      filter: {
        land: '',
        firma: '',
      },
      sortierschluessel: '', // Initialer Sortierschlüssel
      sortierreihenfolge: 1, // 1 = aufsteigend, -1 = absteigend
      currentPage: 1, // Aktuelle Seite
      resultsPerPage: 10, // Ergebnisse pro Seite
    };
  },
  computed: {
    gefilterteDaten() {
      return this.emissionsDaten
        .filter((eintrag) => {
          return (
            eintrag.land.toLowerCase().includes(this.filter.land.toLowerCase()) &&
            eintrag.firma.toLowerCase().includes(this.filter.firma.toLowerCase())
          );
        })
        .sort((a, b) => {
          if (!this.sortierschluessel) return 0;
          if (a[this.sortierschluessel] < b[this.sortierschluessel]) return -1 * this.sortierreihenfolge;
          if (a[this.sortierschluessel] > b[this.sortierschluessel]) return 1 * this.sortierreihenfolge;
          return 0;
        });
    },
    totalPages() {
      return Math.ceil(this.gefilterteDaten.length / this.resultsPerPage);
    },
    paginierteDaten() {
      const start = (this.currentPage - 1) * this.resultsPerPage;
      const end = this.currentPage * this.resultsPerPage;
      return this.gefilterteDaten.slice(start, end);
    },
  },
  methods: {
    datenSortieren(schluessel) {
      // Wenn der gleiche Schlüssel erneut geklickt wird, die Reihenfolge umkehren
      if (this.sortierschluessel === schluessel) {
        this.sortierreihenfolge *= -1;
      } else {
        // Sortierung zurücksetzen und nach dem neuen Schlüssel sortieren
        this.sortierschluessel = schluessel;
        this.sortierreihenfolge = 1;
      }
    },
    changePage(direction) {
      const newPage = this.currentPage + direction;
      if (newPage > 0 && newPage <= this.totalPages) {
        this.currentPage = newPage;
      }
    },
  },
  mounted() {
    // Überprüfe, ob die Daten geladen werden
    console.log(this.emissionsDaten); // Ausgabe der geladenen Daten
  },
};
</script>

<style scoped>
/* Body Container */
.body-container {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  height: 100vh;
  background-image: url('https://images.pexels.com/photos/957024/forest-trees-perspective-bright-957024.jpeg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  color: rgb(7, 3, 3);
  padding-top: 40px;
  position: relative;
  padding-left: 20px; /* Einrückung von der linken Seite */
  padding-right: 20px; /* Einrückung von der rechten Seite */
}

/* Overlay für besseren Textkontrast */
.body-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.3);
  z-index: -1;
}

/* Kopfzeilen */
h1 {
  font-size: 40px;
  font-weight: bold;
  background-color: rgba(255, 255, 255, 0.8);
  margin-top: 20px;
  border-radius: 8px;
  padding: 20px;
  text-align: center;
  color: #1b5e20;
  letter-spacing: 2px;
  margin-left: 20px; /* Einrückung */
  margin-right: 20px; /* Einrückung */
}

h2 {
  font-size: 18px;
  font-weight: normal;
  margin-top: 10px;
  background-color: rgba(72, 141, 86, 0.8);
  border-radius: 15px;
  padding: 15px;
  color: #fff;
  line-height: 1.5;
  margin-left: 20px; /* Einrückung */
  margin-right: 20px; /* Einrückung */
}

/* Filter */
.filter input {
  margin-right: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 20px;
  transition: all 0.3s ease;
  margin-left: 20px; /* Einrückung */
}

.filter input:focus {
  border-color: #48a14e;
  box-shadow: 0 0 8px rgba(72, 161, 78, 0.5);
  outline: none;
}

/* Tabelle */
.table-container {
  margin-top: 30px;
  background-color: rgba(255, 255, 255, 0.9);
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  margin-left: 20px; /* Einrückung */
  margin-right: 20px; /* Einrückung */
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

th,
td {
  padding: 12px;
  text-align: left;
  border: 1px solid #ccc;
}

th {
  cursor: pointer;
  background-color: #4caf50;
  color: white;
}

th.active {
  background-color: #388e3c; /* Hellerer Grünton bei aktivem Sortieren */
}

tr:hover {
  background-color: #f5f5f5;
}

/* Pagination */
.pagination {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

.pagination button {
  padding: 10px;
  margin: 0 5px;
  cursor: pointer;
  background-color: #f2f2f2;
  border: 1px solid #ddd;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.pagination button:hover {
  background-color: #ddd;
}

.pagination button:disabled {
  background-color: #f5f5f5;
  cursor: not-allowed;
}
</style>
