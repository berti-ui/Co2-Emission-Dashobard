<template>
 <div class="body-container">
  <h1>Transparenz für eine nachhaltige Zukunft</h1>
  <p>Wir setzen uns dafür ein, den Klimawandel zu bekämpfen, indem wir Klarheit schaffen: Welche Länder und Unternehmen tragen wie viel zu den globalen CO2-Emissionen bei? Unsere Plattform macht diese Daten sichtbar und zugänglich – für mehr Bewusstsein, Verantwortung und Veränderung. Gemeinsam können wir fundierte Entscheidungen treffen und eine nachhaltigere Welt gestalten. Werde Teil des Wandels und entdecke, wie Transparenz den Weg zu einer besseren Zukunft ebnen kann.</p>
  </div>

</template>

<script scoped>
export default {
    name: 'Body',
  }
</script>

<style scoped>
.body-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh; /* Die Höhe auf die gesamte Ansicht setzen */
  background-image: url('https://images.pexels.com/photos/1179229/pexels-photo-1179229.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2');
  background-size: cover; /* Das Bild vollständig abdecken */
  background-repeat: no-repeat; /* Bild nicht wiederholen */
  background-position: center; /* Das Bild zentrieren */
  color: white; /* Textfarbe anpassen, damit sie auf dem Hintergrund lesbar ist */
  text-align: center;
}

p {
font-size: large;
height: top;

}

h1 {

}


</style>