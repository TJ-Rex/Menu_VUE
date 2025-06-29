<template>
  <div id="app">
    <!-- Navbar y botón de menú -->
    <header>
      <DropdownMenu />
    </header>

    <!-- Contenido principal después del navbar -->
    <main>
      <div class="contenedor">
        <div class="texto descripcion">
          <h1>Ejercicio interactivo con Vue.js</h1>
          <p>
            Lorem ipsum dolor sit amet consectetur, adipisicing elit. Eveniet perspiciatis commodi blanditiis autem at officia cupiditate earum tempora, facilis culpa saepe libero porro officiis ipsum distinctio eligendi consectetur ullam doloribus deleniti labore inventore exercitationem odio nam! Sed, perspiciatis harum unde quam incidunt vero at placeat distinctio quae cumque earum voluptatum odio inventore. Sequi, ea consectetur! Eum ex, odio labore corporis aspernatur mollitia eos suscipit natus fugiat similique repellat architecto. Consectetur, sapiente, beatae asperiores ipsam nobis suscipit minus rem numquam aspernatur cupiditate laborum adipisci corrupti eius fugit in! Ad eius nesciunt porro maiores quaerat recusandae vitae molestiae sequi nobis, incidunt odit.
          </p>
          <!-- Puedes seguir pegando el resto del texto igual que en tu HTML -->
        </div>
      </div>
    </main>

    <!-- Footer, si lo quieres incluir luego -->
  </div>
</template>

<script>
import DropdownMenu from './components/DropdownMenu.vue';

export default {
  name: 'App',
  components: {
    DropdownMenu
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
  padding: 100px 20px 20px; /* para dejar espacio al navbar */
}
</style>
