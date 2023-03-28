<template>
  <header>
    <div class="wrapper">
      <div class="LP"><h1>Listado de Pacientes</h1></div>

      <RouterLink to="/nuevo-paciente">
        <button type="button" class="btn btn-acentoLP">Nuevo paciente</button>
      </RouterLink>

      <RouterLink to="/home-page">
        <button type="button" class="btn btn-secondaryLP">volver</button>
      </RouterLink>
      <div class="container">
        <div class="row">
          <div>
            <table class="table mt-4">
              <thead>
                <tr>
                  <th scope="col">Dni</th>
                  <th scope="col">Nombre</th>
                  <th scope="col">Apellido</th>

                  <th scope="col">Telefono</th>
                  <th scope="col">Domicilio</th>
                </tr>
              </thead>
              <tbody>
                <tr
                  class="text-center"
                  v-for="paciente in pacientes"
                  :key="paciente.codigo"
                >
                  <td scope="row">{{ paciente?.dni }}</td>
                  <td>{{ paciente.nombre }}</td>
                  <td>{{ paciente.apellido }}</td>
                  <td>{{ paciente.telefono }}</td>
                  <td>{{ paciente.calle }},{{ paciente.localidad }}</td>
                  <td>
                    <button
                      type="button"
                      class="btn btn-warning"
                      v-on:click="esEditar(paciente.dni)"
                    >
                      Editar
                    </button>
                  </td>
                  <td>
                    <button
                      type="button"
                      class="btn btn-danger"
                      v-on:click="borraRegistro(paciente.dni)"
                    >
                      Eliminar
                    </button>
                  </td>
                  <td>
                    <button
                      type="button"
                      class="btn btn-info"
                      v-on:click="gestionPaciente(paciente.dni)"
                    >
                      Gestion
                    </button>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </header>
  <body></body>
</template>

<script>
export default {
  data() {
    return {
      pacientes: [],
    };
  },
  mounted() {
    this.consultarPacientes();
  },
  methods: {
    consultarPacientes() {
      fetch("http://localhost:4000/api/pacientes")
        .then((respuesta) => respuesta.json())
        .then((datosRespuesta) => {
          console.log(datosRespuesta);
          this.pacientes = [];
          if (typeof datosRespuesta[0].success === "undefined") {
            this.pacientes = datosRespuesta;
          }
        })
        .catch(console.log);
    },
    esEditar(id) {
      this.$router.push(`/editar-pacientes/${id}`);
    },
    gestionPaciente(id) {
      this.$router.push(`/paciente-tratamiento/${id}`);
    },

    borraRegistro(id) {
      fetch("http://localhost:4000/api/pacientes/" + id, {
        method: "DELETE",
      })
        .then((res) => res.json())
        .then((dataRes) => {
          console.log(dataRes);
        })
        .catch(console.log);

      alert("paciente eliminado");
      location.reload();
    },
  },
};
</script>

<style>

header{
  background-color: #2596be;
}
body{
  background-color: #2596be;
}

.btn-acentoLP {
  font-style: normal;
  font-weight: 500;
  font-size: 25px;
  line-height: 35px;
  color: #FAD8D6;
  text-transform: capitalize;
  text-decoration: none;
  letter-spacing: 0.25px;
  background-color: #EE596D;
  width: 300px;
  height: 45px;
  border-radius: 40px;
  border: none;
  margin: 2% 0% 2% 0%;
  cursor: pointer;
  transition: all 1s ease;
}



.btn-secondaryLP {
  font-style: normal;
  font-weight: 500;
  font-size: 30px;
  line-height: 30px;
  color: #00002E;
  text-transform: capitalize;
  text-decoration: none;
  background-color: #FAD8D6;
  width: 300px;
  height: 45px;
  border-radius: 40px;
  border: none;
  cursor: pointer;
  
  transition: all 1s ease;
}
.btn-primaryLP:hover {
  background-color: #00002E;
}
.btn-secondaryLP:hover {
  background-color: #9FF2F5;
}

.btn-acentoLP:hover {
  background-color: #847996;
}
.LP h1{
  margin-top: 50px;
}

</style>