<template>
  <div>
    <HeaderLogin />
    <div class="container">
      <form action="">
        <div>
          <label>Nombre</label>
          <div class="col-sm-10">
            <input type="text" name="nombre" id="nombre" v-model="form.nombre" />
          </div>
        </div>
        <div>
          <label>Direccion</label>
          <div class="col-sm-10">
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
        <div class="col">
          <label>DNI</label>
          <div class="col-sm-7">
            <input type="text" name="dni" id="dni" v-model="form.dni" />
          </div>
        </div>
        <div>
          <button type="button" v-on:click="guardar()">Guardar</button>
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
  name: 'NuevoUsuario',
  data: function () {
    return {
      form: {
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
  components: {
    HeaderLogin,
    FooterLogin
  },
  methods: {
    guardar() {
      this.form.token = localStorage.getItem('token')
      axios.post('https://api.solodata.es/pacientes', this.form).then((data) => {
        console.log(data)
      })
    },
    salir() {}
  }
}
</script>
<style scoped>
.left {
  text-align: left;
}
</style>
