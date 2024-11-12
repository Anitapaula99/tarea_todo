<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
       
    </p>
    <h3>añadir tareas</h3>
    <ul>
      <li>Permite al usuario ingresar tareas de forma manual</li>
      
    </ul>
    <h3>listas de tareas</h3>
    <ul>
    
      <li>Incluye un botón que, al ser presionado, obtiene tareas desde la API</li>
    </ul>
    <h3>listas combinadas</h3>
    <ul>
      
      <li>Esta sección extrae automáticamente las tareas de la API y permite agregar nuevas tareas al mismo tiempo.</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
