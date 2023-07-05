<template>
  <!-- A ver pringado, suspense utiliza dos slots, el # es para darle un nombre
  el defualt se muestra cuando se carga, y el fallback mientras esta cargando -->
  <Suspense>
    <template #default>
      <Home />
    </template>
    <template #fallback>
      <SplashScreen />  
    </template>
  </Suspense>
</template>


<script>
  import SplashScreen from './components/SplashScreen.vue';
  import { defineAsyncComponent } from 'vue';

  export default {
    components: {
      SplashScreen,
      Home: defineAsyncComponent(() => 
        new Promise((resolve) => {
          setTimeout(() => {
            resolve(import("./components/Home.vue"))
          }, 2500)
        })
      )
    }
  }
</script>

<style>
html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}

* {
  --brand-green: #04b500;
  --brand-blue: #0689b0;
}
</style>
