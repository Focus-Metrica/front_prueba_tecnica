<template>
  <div>
    <HeaderLogin />
    <div class="container">
      <form action="">
        <div>
          <label>Nombre</label>
          <div>
            <input type="text" name="nombre" id="nombre" v-model="form.nombre" />
          </div>
        </div>
        <div>
          <label for="" class="control-label col-sm-2">Direccion</label>
          <div>
            <input type="text" name="direccion" id="direccion" v-model="form.direccion" />
          </div>
        </div>
        <div>
          <div class="col">
            <label>Correo</label>
            <div class="col-sm-7">
              <input type="text" name="correo" id="correo" v-model="form.correo" />
            </div>
          </div>
          <div class="col">
            <label>codigo Postal</label>
            <div class="col-sm-7">
              <input
                type="text"
                name="codigopostal"
                id="codigopostal"
                v-model="form.codigoPostal"
              />
            </div>
          </div>
        </div>
        <div>
          <div class="col">
            <label>Genero</label>
            <div class="col-sm-7">
              <input type="text" name="genero" id="genero" v-model="form.genero" />
            </div>
          </div>
          <div class="col">
            <label>Telefono</label>
            <div class="col-sm-7">
              <input type="text" name="telefono" id="telefono" v-model="form.telefono" />
            </div>
          </div>
        </div>
        <div>
          <label>Fecha nacimiento</label>
          <div class="col-sm-4">
            <input
              type="text"
              name="fechanacimineto"
              id="telefono"
              v-model="form.fechaNacimiento"
            />
          </div>
        </div>
        <div>
          <button type="button" v-on:click="editar()">Editar</button>
          <button type="button" v-on:click="eliminar()">Eliminar</button>
          <button type="button" v-on:click="salir()">Salir</button>
        </div>
      </form>
    </div>
    <FooterLogin />
  </div>
</template>
<script>
import HeaderLogin from '@/components/HeaderLogin.vue'
import FooterLogin from '@/components/FooterLogin.vue'
import axios from 'axios'
export default {
  name: 'EditarUsuario',
  components: {
    HeaderLogin,
    FooterLogin
  },
  data: function () {
    return {
      form: {
        pacienteId: '',
        nombre: '',
        dni: '',
        correo: '',
        codigoPostal: '',
        genero: '',
        telefono: '',
        fechaNacimiento: '',
        token: ''
      }
    }
  },
  methods: {
    editar() {
      axios.put('https://api.solodata.es/pacientes', this.form).then((data) => {
        console.log(data)
      })
    },
    salir() {
      this.$router.push('/dashboard')
    },
    eliminar() {
      var enviar = {
        paciente: this.form.pacienteId,
        token: this.form.token
      }
      axios.delete('https://api.solodata.es/pacientes', { header: enviar }).then((data) => {
        console.log(data)
        this.$router.push('/dashboard')
      })
    }
  },
  mounted: function () {
    this.form.pacienteId = this.$route.params.id
    axios.get('https://api.solodata.es/pacientes?id=' + this.form.pacienteId).then((data) => {
      this.form.nombre = data.data[0].Nombre
      this.for.dni = data.data[0].DNI
      this.form.correo = data.data[0].Correo
      this.form.codigoPostal = data.data[0].CodigoPostal
      this.form.genero = data.data[0].Genero
      this.form.telefono = data.data[0].Telefono
      this.form.fechaNacimiento = data.data[0].FechaNacimiento
      this.form.token = localStorage.getItem('token')
    })
  }
}
</script>
<style scoped>
.left {
  text-align: left;
}
</style>
