<template>
  <div>
    <HeaderLogin />

    <div>
      <button v-on:click="nuevo()">Nuevo Paciente</button>

      <table>
        <thead>
          <tr>
            <th scope="col">ID</th>
            <th scope="col">Nombre</th>
            <th scope="col">DNI</th>
            <th scope="col">Teléfono</th>
            <th scope="col">Correo</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="paciente in Listapacientes"
            :key="paciente.PacienteId"
            v-on:click="editar(paciente.PacienteId)"
          >
            <th scope="row">{{ paciente.PacienteId }}</th>
            <td>{{ paciente.Nombre }}</td>
            <td>{{ paciente.DIN }}</td>
            <td>{{ paciente.Telefono }}</td>
            <td>{{ paciente.Correo }}</td>
          </tr>
        </tbody>
      </table>
    </div>

    <FooterLogin />
  </div>
</template>

<script>
import HeaderLogin from '@/components/HeaderLogin.vue'
import FooterLogin from '@/components/FooterLogin.vue'
import axios from 'axios'
export default {
  name: 'DashBoard',
  data() {
    return {
      Listapacientes: null,
      pagina: 1
    }
  },
  components: {
    HeaderLogin,
    FooterLogin
  },
  methods: {
    editar(id) {
      this.$router.push('/editar/' + id)
    },
    nuevo(id) {
      this.$router.push('/nuevo/' + id)
    }
  },
  mounted: function () {
    let direction = 'https://api.solodata.es/pacientes?page=' + this.pagina
    axios.get(direction).then((data) => {
      this.Listapacientes = data.data
    })
  }
}
</script>

<style scoped>
.left {
  margin-bottom: 15px;
  text-align: left;
}
</style>
