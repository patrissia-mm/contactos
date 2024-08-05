<template>
  <div>
    <h1>{{ title }}</h1>
    <table>
      <thead>
        <tr>
          <th>Id</th>
          <th>Nombre</th>
          <th>E-mail</th>
          <th>Dirección</th>
          <th>Teléfono</th>
          <th>País</th>
          <th>Ciudad</th>
          <th></th>
        </tr>
        <tr>
          <th><input type="text" v-model="contactoNuevo.id" /></th>
          <th><input type="text" v-model="contactoNuevo.name" /></th>
          <th><input type="text" v-model="contactoNuevo.email" /></th>
          <th><input type="text" v-model="contactoNuevo.address" /></th>
          <th><input type="text" v-model="contactoNuevo.phone" /></th>
          <th><input type="text" v-model="contactoNuevo.country" /></th>
          <th><input type="text" v-model="contactoNuevo.city" /></th>
          <th><button @click="guardarNuevo()">Nuevo Contacto</button></th>
        </tr>
        <tr v-if="indexAEditar !== null">
          <th><input type="text" v-model="contactoEditado.id" /></th>
          <th><input type="text" v-model="contactoEditado.name" /></th>
          <th><input type="text" v-model="contactoEditado.email" /></th>
          <th><input type="text" v-model="contactoEditado.address" /></th>
          <th><input type="text" v-model="contactoEditado.phone" /></th>
          <th><input type="text" v-model="contactoEditado.country" /></th>
          <th><input type="text" v-model="contactoEditado.city" /></th>
          <th><button @click="guardarEdicion()">Guardar cambios</button></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(contacto, index) in contactos" :key="contacto.id">
          <td>{{ contacto.id }}</td>
          <td>{{ contacto.name }}</td>
          <td>{{ contacto.email }}</td>
          <td>{{ contacto.address }}</td>
          <td>{{ contacto.phone }}</td>
          <td>{{ contacto.country }}</td>
          <td>{{ contacto.city }}</td>
          <td>
            <button @click="eliminarContacto(index)">Eliminar</button>
            <button @click="editarContacto(contacto, index)">Editar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "MiComponente",
  data() {
    return {
      title: "Agenda de Contactos",
      indexAEditar: null,
      contactoNuevo: {
        id: null,
        name: "",
        email: "",
        address: "",
        phone: "",
        country: "",
        city: "",
      },
      contactoEditado: {
        id: null,
        name: "",
        email: "",
        address: "",
        phone: "",
        country: "",
        city: "",
      },
      contactos: [
        {
          id: 1,
          name: "Alice Johnson",
          email: "alice.johnson@example.com",
          address: "123 Maple Street",
          phone: "123-456-7890",
          country: "USA",
          city: "New York",
        },
        {
          id: 2,
          name: "Bob Smith",
          email: "bob.smith@example.com",
          address: "456 Oak Avenue",
          phone: "987-654-3210",
          country: "Canada",
          city: "Toronto",
        },
        {
          id: 3,
          name: "Carol White",
          email: "carol.white@example.com",
          address: "789 Pine Road",
          phone: "555-123-4567",
          country: "UK",
          city: "London",
        },
        {
          id: 4,
          name: "David Brown",
          email: "david.brown@example.com",
          address: "321 Elm Street",
          phone: "444-555-6666",
          country: "Australia",
          city: "Sydney",
        },
        {
          id: 5,
          name: "Emily Davis",
          email: "emily.davis@example.com",
          address: "654 Spruce Lane",
          phone: "333-444-5555",
          country: "USA",
          city: "Los Angeles",
        },
      ],
    };
  },
  components: {
    // Registro de componentes que se utilizaran.
  },
  methods: {
    guardarNuevo() {
      this.contactos.push(Object.assign({}, this.contactoNuevo));
    },
    eliminarContacto(index) {
      this.contactos.splice(index, 1);
    },
    guardarEdicion() {
      this.contactos[this.indexAEditar] = Object.assign(
        {},
        this.contactoEditado
      );
      this.indexAEditar = null;
    },
    editarContacto(contacto, index) {
      this.indexAEditar = index;
      this.contactoEditado = Object.assign({}, contacto);
    },
  },
  computed: {
    // propiedades computadas que dependen de otras propiedades reactivas
  },
  props: {
    // propiedades que el componente puede recibir.
  },
  emits: [], // los eventos personalizados que el componente puede emitir.
};
</script>

<style scope>
h1 {
  color: #42b983;
}
table {
  width: 100%;
  border-collapse: collapse;
}
th,
td {
  border: 1px solid #ddd;
  padding: 8px;
}
th {
  background-color: f2f2f2;
  text-align: left;
}
</style>
