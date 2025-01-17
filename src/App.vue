<template>
  <div class="app-container">
  <Header></Header>
  <Body></Body>
  <router-view/>
  <Footer></Footer>


  </div>
  </template>


<script>
  import Header from '@/components/Header.vue'
  import Footer from '@/components/Footer.vue'
  import Body from '@/components/Body.vue'
  export default {
    components: {
      Header,
      Body,
      Footer,
      
    }
  }
</script>

<style>

/* Standard Layout für größere Bildschirme */
.app-container {
  display: flex;
  flex-direction: column; /* Stapelt die Komponenten vertikal */
  min-height: 100vh; /* Stellt sicher, dass die Seite immer den ganzen Bildschirm ausfüllt */
}

/* Responsiv für kleine Bildschirmgrößen (Handys) */
@media (max-width: 768px) {
  .app-container {
    padding: 10px; /* Kleinerer Abstand auf Handys */
  }

  /* Der Header wird bei kleinen Bildschirmen horizontal zentriert */
  Header {
    text-align: center;
  }

  /* Beispiel für die Body-Komponente */
  Body {
    padding: 5px; /* Weniger Padding auf Handys */
  }

  Footer {
    padding: 10px;
  }
}

/* Zusätzliche Anpassung für sehr kleine Bildschirme (z.B. Portrait-Modus auf Handys) */
@media (max-width: 480px) { 
  Header {
    font-size: 16px; /* Kleinere Schrift auf mobilen Geräten */
  }}

  Body img {
    width: 100%; /* Bild auf mobilen Geräten auf die gesamte Bildschirmbreite setzen */
  }

body{
  margin: 0;
}
</style>