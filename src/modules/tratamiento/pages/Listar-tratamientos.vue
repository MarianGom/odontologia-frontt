<template>
  <header>
    <div class="wrapper">
      <h1>TRATAMIENTOS</h1>

      <RouterLink to="/nuevo-tratamiento">
        <button type="button" class="btn-acento">Nuevo tratamiento</button>
      </RouterLink>

      <RouterLink to="/home-page">
        <button type="button" class="btn-secondary">volver</button>
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