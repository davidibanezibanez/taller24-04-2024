<template>

  <div class="usuarios">

    <h1>Usuarios</h1>
    
    <ul>
      <li v-for="(nombre, index) in nombres" :key="index">
        {{ nombre }}
        <button @click="modificarUsuario(index)">Modificar Usuario</button>
        <button @click="eliminarUsuario(index)">Eliminar Usuario</button>
      </li>
    </ul>

    <form @submit.prevent="agregarNombre">
      <input v-model="nuevoNombre" placeholder="Ingrese nombre y apellido" />
      <button type="submit">Agregar Usuario</button>
    </form>

  </div>

</template>

<script>

export default {
  data() {
    return {
      nuevoNombre: "",
      nombres: ["David Ibáñez"],
    };
  },
  methods: {
    agregarNombre() {
      if (this.nuevoNombre) {
        this.nombres.push(this.nuevoNombre);
        this.nuevoNombre = "";
      }
    },
    modificarUsuario(index) {
      const actualizarNombre = prompt("Modificar usuario:", this.nombres[index]);
      if (actualizarNombre) {
        this.nombres[index] = actualizarNombre;
      }
    },
    eliminarUsuario(index) {
      if (confirm("¿Desea eliminar este usuario?")) {
        this.nombres.splice(index, 1);
      }
    },
  },
};

</script>

<style>

  .usuarios{
    background-color: rgb(27, 197, 24);
    border-radius: 100px;
    padding: 30px;
  }

</style>
