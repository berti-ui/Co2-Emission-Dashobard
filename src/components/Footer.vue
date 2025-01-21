<template>
  <div>
    <footer>
      <h1>Rechtliche Hinweise</h1>
      <h2>Haftung für Inhalte</h2>
      <p>
        Als Diensteanbieter sind wir gemäß § 7 Abs. 1 TMG für eigene Inhalte auf diesen Seiten nach den allgemeinen Gesetzen verantwortlich.
        Nach §§ 8 bis 10 TMG sind wir jedoch nicht verpflichtet, übermittelte oder gespeicherte fremde Informationen zu überwachen oder nach
        Umständen zu forschen, die auf eine rechtswidrige Tätigkeit hinweisen. Verpflichtungen zur Entfernung oder Sperrung der Nutzung von
        Informationen nach den allgemeinen Gesetzen bleiben hiervon unberührt. Eine diesbezügliche Haftung ist jedoch erst ab dem Zeitpunkt
        der Kenntnis einer konkreten Rechtsverletzung möglich. Bei Bekanntwerden von entsprechenden Rechtsverletzungen werden wir diese Inhalte
        umgehend entfernen.
      </p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'Footer',
};
</script>

<style scoped>
footer {
  background: linear-gradient(135deg, #6a6a6a, #a7a4a6);
  color: white;
  padding: 40px;
  text-align: left;
  width: 100%;
  box-sizing: border-box;
  font-size: 14px;
  position: relative;
}

footer h1 {
  font-size: 24px;
  margin-bottom: 10px;
}

footer h2 {
  font-size: 18px;
  margin-bottom: 20px;
  color: #ffcc00;
}

footer p {
  line-height: 1.6;
  margin-bottom: 20px;
}

footer a {
  color: #007bff;
  text-decoration: none;
}

footer a:hover {
  text-decoration: underline;
}

footer::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 10px;
  background-color: #333;
}
</style>
