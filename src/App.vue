<template>
  <div>
  <Header></Header>
  <router-view/>
  </div>

  


</template>


<script>
  export default {
    name: 'Header',
  }
</script>

<style>
body{
margin: 0;
}


/* Kriterien für das Suchfeld */
input {
border: 0;
border-radius: 8px;
width: 80%;
height: 40px;

}

</style>
