<template>
  <div class="registro">
    <h2>Registro de Usuario</h2>
    <form @submit.prevent="registrarUsuario">
      <input v-model="nombre" type="text" placeholder="Nombre" />
      <span v-if="errores.nombre" class="error">{{ errores.nombre }}</span>

      <input v-model="apellido" type="text" placeholder="Apellido" />
      <span v-if="errores.apellido" class="error">{{ errores.apellido }}</span>

      <input v-model="correo" type="email" placeholder="Correo electrónico" />
      <span v-if="errores.correo" class="error">{{ errores.correo }}</span>

      <input v-model="contrasena" type="password" placeholder="Contraseña" />
      <span v-if="errores.contrasena" class="error">{{ errores.contrasena }}</span>

      <button type="submit">Registrarse</button>
    </form>

    <p v-if="mensaje" :style="{ color: exito ? 'green' : 'red' }">
      {{ mensaje }}
    </p>

    <hr />

    <h3>Usuarios Registrados:</h3>
    <ul>
      <li v-for="(usuario, index) in usuarios" :key="index">
        {{ usuario.nombre }} {{ usuario.apellido }} ({{ usuario.correo }})
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'RegistroUsuario',
  data() {
    return {
      nombre: '',
      apellido: '',
      correo: '',
      contrasena: '',
      usuarios: [],
      mensaje: '',
      exito: false,
      errores: {} // ← errores por campo
    };
  },
  methods: {
    registrarUsuario() {
      this.errores = {}; // limpiar errores previos
      this.exito = false;

      // Validación individual
      if (!this.nombre.trim()) {
        this.errores.nombre = 'El nombre es obligatorio.';
      }

      if (!this.apellido.trim()) {
        this.errores.apellido = 'El apellido es obligatorio.';
      }

      if (!this.correo.trim()) {
        this.errores.correo = 'El correo es obligatorio.';
      } else if (!this.validarCorreo(this.correo)) {
        this.errores.correo = 'El correo no es válido.';
      }

      if (!this.contrasena) {
        this.errores.contrasena = 'La contraseña es obligatoria.';
      } else if (this.contrasena.length <= 4) {
        this.errores.contrasena = 'Debe tener más de 4 caracteres.';
      }

      // Si hay errores, no continúa
      if (Object.keys(this.errores).length > 0) {
        this.mensaje = 'Corrige los errores antes de continuar.';
        return;
      }

      const nuevoUsuario = {
        nombre: this.nombre,
        apellido: this.apellido,
        correo: this.correo,
        contrasena: this.contrasena
      };

      this.usuarios.push(nuevoUsuario);
      this.mensaje = 'Usuario registrado exitosamente';
      this.exito = true;

      // Limpiar formulario
      this.nombre = '';
      this.apellido = '';
      this.correo = '';
      this.contrasena = '';
    },
    validarCorreo(correo) {
      // Validación básica de email
      return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(correo);
    }
  }
};
</script>

<style scoped>
.registro {
  max-width: 400px;
  width: 100%;
  padding: 20px;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 10px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
}

input {
  display: block;
  width: 97%;
  margin: 10px 0 5px;
  padding: 8px;
  border-radius: 5px;
  border: none;
}

.error {
  color: #ff6b6b;
  font-size: 13px;
  margin-bottom: 10px;
  display: block;
}

button {
  padding: 10px;
  background-color: #42b983;
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 5px;
  margin-top: 10px;
}
</style>