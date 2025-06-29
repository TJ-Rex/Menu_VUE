<!-- src/components/DropdownMenu.vue -->
<template>
  <div>
    <nav class="navbar">
        <button class="menu-btn" @click="mostrarMenu = !mostrarMenu">☰ Menú</button>
    </nav>
    <div class="main-content">
        <transition name="slide">
        <div v-if="mostrarMenu" class="sidebar">
            <a href="#">Inicio</a>
            <a href="#">Historial</a>
            <a href="#">Lista de reproducción</a>
            <a href="#">Suscripciones</a>
            <a href="#">Configuración</a>
            <a href="#">Ayuda</a>
        </div>
        </transition>
    </div>
  </div>
</template>


<script>
export default {
  name: 'DropdownMenu',
  data() {
    return {
      mostrarMenu: false
    };
  },
    mounted() {
    document.addEventListener('click', this.handleClickOutside);
    },
    beforeUnmount() {
    document.removeEventListener('click', this.handleClickOutside);
    },
    methods: {
    handleClickOutside(event) {
        const menu = this.$el.querySelector('.sidebar');
        const button = this.$el.querySelector('.menu-btn');
        if (
        this.mostrarMenu &&
        !menu.contains(event.target) &&
        !button.contains(event.target)
        ) {
        this.mostrarMenu = false;
        }
    }
    }
};
</script>

<style scoped>

.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #2e2b3a;
  padding: 10px 20px;
  box-shadow: 0 0 10px #8a2be2;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 2000;
}

.titulo-navbar {
  color: #ffffff;
  font-size: 20px;
  margin: 0;
}

.menu-btn {
  background-color: #2e2b3a;
  color: white;
  padding: 12px 20px;
  font-size: 16px;
  border: none;
  cursor: pointer;
  box-shadow: 0 0 10px #8a2be2;
  border-radius: 5px;
}

.sidebar {
  position: fixed;
  top: 0;
  left: 0;
  width: 220px;
  height: 100%;
  background-color: #1e1b2e;
  box-shadow: 2px 0 10px rgba(0, 0, 0, 0.3);
  padding: 20px;
  display: flex;
  flex-direction: column;
  z-index: 3000; /* <--- antes estaba en 1000, ahora está encima del navbar */
}


.sidebar a {
  color: #fff;
  padding: 12px 10px;
  text-decoration: none;
  font-weight: bold;
  border-radius: 5px;
  transition: background 0.3s ease;
}

.sidebar a:hover {
  background-color: #8a2be2;
}

/* Transición para deslizar */
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.3s ease;
}
.slide-enter-from,
.slide-leave-to {
  transform: translateX(-100%);
}
</style>
