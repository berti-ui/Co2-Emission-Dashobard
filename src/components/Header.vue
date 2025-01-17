<template>
  <div>
    <header>
      <div>
<input placeholder="Suche">
      </div>
      <div><button><img src="https://cdn-icons-png.flaticon.com/128/7216/7216128.png" alt=""></button></div>

</header>  
    
  </div>
</template>

<script>
  export default {
    name: 'Header',
  }
</script>

<style scoped>

body {
  margin: 0;
  padding: 0;
  height: 100%;
  display: flex;
  flex-direction: column;
}

/* Kriterien für den Header immer wichtog: scoped in Komponenten. So ist der Style nur für diese Komponente verfügbar*/
header {
  background-color: rgb(72, 141, 86);
  height: 120px; 
  padding: 16px;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  box-sizing: border-box;
 
}




/* Kriterien für das Suchfeld */
input {
border: 0;
border-radius: 8px;
width: 200px;
height: 50px;
display: flex;
align-items: center;

}

button { 
      border: 0;
      width: 40%;
      height: 40%;
      border-radius: 8px;
      align-content: flex-end;
    }


</style>,