<template>
  <header>
    <div class="wrapper">
      <div class="LT"><h1>TRATAMIENTOS</h1></div>
      

      <RouterLink to="/nuevo-tratamiento">
        <button type="button" class="btn btn-infoLT">Nuevo tratamiento</button>
      </RouterLink>

      <RouterLink to="/home-page">
        <button type="button" class="btn btn-secondaryLT">volver</button>
      </RouterLink>

      <nav>
        <table class="table">
          <thead>
            <tr>
              <th scope="col">Codigo</th>
              <th scope="col">Nombre</th>
              <th scope="col">Descripcion</th>

              <th scope="col">Precio</th>
              <th scope="col">Duracion</th>
            </tr>
          </thead>
          <tbody>
            <tr
              class="text-center"
              v-for="tratamiento in tratamientos"
              :key="tratamiento.codigo"
            >
              <td scope="row">{{ tratamiento?.codigo }}</td>
              <td>{{ tratamiento.nombre }}</td>
              <td>{{ tratamiento.descripcion }}</td>
              <td>{{ tratamiento.precio }}</td>
              <td>{{ tratamiento.duracion }}</td>
              <td>
                <button
                  type="button"
                  class="btn btn-warning"
                  v-on:click="esEditar(tratamiento.codigo)"
                >
                  Editar
                </button>
              </td>
              <td>
                <button
                  type="button"
                  class="btn btn-danger"
                  v-on:click="borraRegistro(tratamiento.codigo)"
                >
                  Eliminar
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </nav>


      
    </div>
  </header>


  
</template>

<script>
export default {
  data() {
    return {
      tratamientos: [],
    };
  },
  mounted() {
    this.consultarTratamientos();
  },
  methods: {
    consultarTratamientos() {
      fetch("http://localhost:4000/api/tratamientos")
        .then((respuesta) => respuesta.json())
        .then((datosRespuesta) => {
          console.log(datosRespuesta);
          this.tratamientos = [];
          if (typeof datosRespuesta[0].success === "undefined") {
            this.tratamientos = datosRespuesta;
          }
        })
        .catch(console.log);
    },
    esEditar(id) {
      this.$router.push(`/editar-tratamientos/${id}`);
    },

    borraRegistro(id) {
      fetch("http://localhost:4000/api/tratamientos/" + id, {
        method: "DELETE",
      })
        .then((res) => res.json())
        .then((dataRes) => {
          console.log(dataRes);
        })
        .catch(console.log)

      alert("tratamiento eliminado")
      location.reload()
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

.btn-infoLT {
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



.btn-secondaryLT {
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
.btn-primaryLT:hover {
  background-color: #00002E;
}
.btn-secondaryLT:hover {
  background-color: #9FF2F5;
}

.btn-acentoLT:hover {
  background-color: #847996;
}
.LT h1{
  margin-top: 50px;
}

</style>