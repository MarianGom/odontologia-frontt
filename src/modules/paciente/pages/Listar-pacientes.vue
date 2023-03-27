<template>
  <header>
    <div class="wrapper">
      <h1>Listado de Pacientes</h1>

      <RouterLink to="/nuevo-paciente">
        <button type="button" class="btn-acento">Nuevo paciente</button>
      </RouterLink>

      <RouterLink to="/home-page">
        <button type="button" class="btn-secondary">volver</button>
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
  <body>

  </body>
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

.wrapper {
    margin-top: 50px;
    background-color: #00A6D0;
  
}
body {
    background-color: #00A6D0;
  
}
.btn-acento {
    font-style: normal;
    font-weight: 500;
    font-size: 25px;
    color: #FAD8D6;
    text-transform: capitalize;
    text-decoration: none;
    letter-spacing: 0.25px;
    background-color: #EE596D;
    width: 250px;
    height: 60px;
    border-radius: 40px;
    border: none;
    margin: 2% 0% 2% 0%;
    cursor: pointer;
    transition: all 1s ease;  
}
.btn-secondary {
    font-style: normal;
    font-weight: 500;
    font-size: 25px;
    color: #00002E;
    text-transform: capitalize;
    text-decoration: none;
    letter-spacing: 0.25px;
    background-color: #FAD8D6;
    width: 250px;
    height: 60px;
    border-radius: 40px;
    border: none;
    margin: 2% 0% 2% 0%;
    cursor: pointer;
    transition: all 1s ease;
}
</style>