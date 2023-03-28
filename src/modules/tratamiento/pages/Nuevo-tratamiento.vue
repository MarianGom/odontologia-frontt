<template>
  <div class="flex-containerNT">
    <div class="contenido-headerNT">
      <nav class="nav">
        <ul id="links">

          <li>
            <RouterLink to="/home-page">Inicio</RouterLink>
          </li>
          <li>
            <RouterLink to="/listar-pacientes">Pacientes</RouterLink>
          </li>
          <li>
            <RouterLink to="/listar-tratamientos">Tratamientos</RouterLink>
          </li>
        </ul>
      </nav>
      <nav class="nav2">
        <div class="buscar">
        </div>
        <div class="icono-nav">
        </div>
      </nav>
    </div>
    <div class="sidebarNT">
    </div>

    <div class="mainNT">
      <div class="main-containerNT">

        <div class="NT">
          <h1>Nuevo Tratamiento</h1>
        </div>

        <div class="tituloNT"></div>
        <div class="formularioNT">
          <form class="" v-on:submit.prevent="agregarRegistro">
            <div class="datosNT">

              <div class="col1NT">
                <div class="mb-3">
                  <input type="number" class="form-control" v-model="tratamiento.codigo" id="codigo" name="codigo"
                    placeholder="Codigo" required />
                  <small id="helpId" class="form-text text-muted">Codigo de Tratamiento</small>
                </div>
              </div>
              <div class="col2NT">
                <div class="mb-3">
                  <input type="text" class="form-control" v-model="tratamiento.nombre" id="nombre" name="nombre"
                    placeholder="Nombre" required />
                  <small id="helpId" class="form-text text-muted">Nombre del tratamiento</small>
                </div>
              </div>
            </div>


            <div class="descripcion">
              
              <div class="tituloNT"></div>
              <div class="col1NT">
                <div class="mb-3">
                  <input type="text" class="form-control" v-model="tratamiento.descripcion" id="descripcion"
                    name="descripcion" placeholder="Descripcion" required />
                  <small id="helpId" class="form-text text-muted">Descripcion del tratamiento</small>
                </div>
              </div>

            </div>

            <div class="precio">
              
              <div class="tituloNT"></div>
              <div class="col1NT">
                <div class="mb-3">
                  <input type="number" class="form-control" v-model="tratamiento.precio" id="precio" name="precio"
                    placeholder="Precio" required />
                  <small id="helpId" class="form-text text-muted">Precio del tratamiento</small>
                </div>
                <div class="mb-3">
                  <input type="text" class="form-control" v-model="tratamiento.duracion" id="duracion" name="duracion"
                    placeholder="Duracion" required />
                  <small id="helpId" class="form-text text-muted">Duracion del tratamiento</small>
                </div>
              </div>
            </div>

            <div class="menu-izqNT">
              <button type="submit" class="btn btn-acentoNT">Agregar</button>
              <RouterLink to="/listar-tratamientos">
                <button type="button" class="btn btn-secondaryNT">
                  cancelar
                </button>
              </RouterLink>
            </div>
          </form>
        </div>
      </div>

    </div>
  </div>



</template>

<script>
import { } from "@/modules/tratamiento/pages/Listar-tratamientos.vue";
export default {
  name: "Nuevo-tratamiento",

  data() {
    return {
      tratamiento: {},
    };
  },
  methods: {
    async agregarRegistro() {
      console.log(this.tratamiento);

      var datosEnviar = {
        codigo: this.tratamiento.codigo,
        nombre: this.tratamiento.nombre,
        descripcion: this.tratamiento.descripcion,
        precio: this.tratamiento.precio,
        duracion: this.tratamiento.duracion,
      };

      console.log(datosEnviar);

      await fetch("http://localhost:4000/api/tratamientos", {
        method: "POST",
        body: JSON.stringify(datosEnviar),
        headers: {
          "Content-Type": "application/json",
        },
      })
        .then((res) => res.json())
        .catch((error) => console.error("Error", error))
        .then((response) => console.log("Success", response));

      alert("tratamiento registrado");
      this.$router.push("/listar-tratamientos");
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}


.flex-containerNT {
  display: flex;
  background-color: #2596be;
  flex-flow: row wrap;
  text-align: center;
}

.contenido-headerNT {

  background-color: #FAD8D6;
  width: 100%;
  height: 60px;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: space-between;
  align-content: center;
}

.mainNT {
    display: flex;
    flex-direction: row-reverse;
    justify-content: flex-end;
    width: 90%;
    background-size: cover;
    align-items: center;
}

.main-containerNT {
  width: 100%;
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  margin-left: 150px;


}

.sidebarNT {
  background: #FAD8D6;
  width: 50px;
  height: 100vh;
  position: fixed;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.mainNT .main-containerNT .menu-izqNT a {
  display: flex;
  align-items: center;
  justify-content: center;

}

.menu-izqNT {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-content: center;
  align-items: center;
  text-align: center;
  margin-top: 50px;
}

.tituloNT {
  font-size: 30px;
  font-weight: 500;
  letter-spacing: 0.56px;
  margin-left: 64px;
  margin-top: 30px;
  text-align: initial;
}

.formularioNT {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.datosNT {
  display: flex;
  flex-direction: row;
  margin-top: 30px;
  justify-content: space-between;
}

.descripcion .col1NT {
  display: flex;
  flex-direction: row;
  margin-top: 20px;
  margin-left: 92px;
}
#descripcion{
  width: 800px;
}
#duracion{
width: 200px;
}

#precio{
  width: 200px;
}
.precio .col1NT {
  display: flex;
  flex-direction: row;
  margin-top: 20px;
  margin-left: 92px;
  margin-right: 800px;
  justify-content: space-between;
}

.col1NT {

  display: flex;
  flex-direction: column;
  margin-left: 92px;
}

.col2NT {

  display: flex;
  flex-direction: column;
  margin-right: 900px
}
#codigo{
  width: 200px;
}
#nombre{
  margin-left: 100px;
  width: 500px;
}

.contenido-headerNT nav ul {
  list-style: none;
  display: flex;
  margin-left: 70px;
  margin-top: 15px;

}

.contenido-headerNT .nav2 {
  display: flex;
  justify-content: space-between;
  align-items: center;

}

.contenido-headerNT nav ul li a {
  text-decoration: none;
  color: #00002E;
  margin: 0px 18px;
  font-weight: 500;
  font-size: 20px;
  line-height: 20px;
  letter-spacing: 0.1px;
}



.mainNT .btn-acentoNT {
  font-style: normal;
  font-weight: 500;
  font-size: 30px;
  line-height: 35px;
  color: #FAD8D6;
  text-transform: uppercase;
  text-decoration: none;
  letter-spacing: 0.25px;
  background-color: #EE596D;
  width: 409px;
  height: 67px;
  border-radius: 40px;
  border: none;
  margin: 2% 0% 2% 0%;
  cursor: pointer;
  transition: all 1s ease;
}

.btn-secondaryNT {
  font-style: normal;
  font-weight: 500;
  font-size: 30px;
  line-height: 30px;
  color: #00002E;
  text-transform: uppercase;
  text-decoration: none;
  background-color: #FAD8D6;
  width: 409px;
  height: 67px;
  border-radius: 40px;
  border: none;
  cursor: pointer;
}


.btn-primary {
  font-style: normal;
  font-weight: 500;
  font-size: 30px;
  line-height: 35px;
  color: #00002E;
  text-transform: uppercase;
  background: #9FF2F5;
  height: 67px;
  width: 409px;
  border-radius: 40px;
  border: none;
  margin: 1% 0% 1% 0%;
  cursor: pointer;
  transition: all 1s ease;
}

.datosNT .btn-primary {
  font-size: 20px;
  text-transform: capitalize;
  height: 48px;
  width: 300px;
  border-radius: 30px;
  padding-left: 27px;
}

.descripcion .btn-primary {
  font-size: 20px;
  text-transform: capitalize;
  height: 48px;
  width: 89px;
  border-radius: 30px;
  padding-left: 27px;
  margin-right: 10px;
}

.precio .btn-primary {
  font-size: 20px;
  text-transform: capitalize;
  height: 48px;
  width: 272px;
  border-radius: 30px;
  padding-left: 27px;
  margin-right: 500px;
}

.NT h1 {

  font-size: 2rem;
  text-align: end;
  margin-right: 180px;
  margin-top: 10px;
}
</style>


