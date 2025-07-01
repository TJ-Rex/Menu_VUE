<template>
  <div id="app">
    <header>
      <DropdownMenu />
    </header>

    <main>
      <div class="contenedor">
        <div class="texto descripcion">
          <h1>Ejercicio interactivo con Vue.js</h1>
          <div class="registro-wrapper">
            <RegisterUser />
          </div>
        </div>
      </div>
    </main>

  </div>
</template>

<script>
import DropdownMenu from './components/DropdownMenu.vue';
import RegisterUser from './components/RegisterUser.vue';


export default {
  name: 'App',
  components: {
    DropdownMenu,
    RegisterUser
  }
};
</script>

<style>
body, html {
  margin: 0;
  padding: 0;
  background-color: #1e1b2e;
  font-family: Arial, sans-serif;
  color: white;
  height: 100%;
}
main {
  padding: 70px 20px 20px; 
}

.registro-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

</style>