<template>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.1/css/all.min.css"
    integrity="sha512-MV7K8+y+gLIBoVD59lQIYicR65iaqukzvf/nwasF0nqhPay5w/9lJmVM2hMDcnK1OnMGCdVK+iQrJ7lzPJQd1w=="
    crossorigin="anonymous" referrerpolicy="no-referrer" />

  <div class="flex-containerNP">
    <div class="contenido-headerNP">
      <nav class="navNP">
        <ul id="linksNP">
          
          <li><RouterLink to="/home-page">Inicio</RouterLink></li>
          <li><RouterLink to="/listar-pacientes">Pacientes</RouterLink></li>
          <li><RouterLink to="/listar-tratamientos">Tratamientos</RouterLink></li>
        </ul>
      </nav>
      <nav class="nav2NP">
        <div class="buscarNP">
        </div>
        <div class="icono-nav">
        </div>
      </nav>
    </div> <div class="sidebarNP">
      </div>


    <div class="mainNP">
      <div class="main-containerNP">
        <div class="NP"> <h1>Nuevo Paciente</h1></div>
        <div class="tituloNP">DATOS PERSONALES</div>
        <div class="formularioNP">
          <form class="" v-on:submit.prevent="agregarRegistro">
            <div class="datosNP">
              <div class="col1NP">
                <div class="mb-3">
                  <input type="number" class="form-control" v-model="paciente.dni" id="dni" name="dni" placeholder="Dni"
                    required />
                  <small id="helpId" class="form-text text-muted">Dni del paciente</small>
                </div>
                <div class="mb-3">
                  <input type="text" class="form-control" v-model="paciente.nombre" id="nombre" name="nombre"
                    placeholder="Nombre" required />
                  <small id="helpId" class="form-text text-muted">Nombre del paciente</small>
                </div>
              </div>
              <div class="col2NP">
                <div class="mb-3">
                  <input type="text" class="form-control" v-model="paciente.apellido" id="apellido" name="apellido"
                    placeholder="Apellido" required />
                  <small id="helpId" class="form-text text-muted">Apellido del Paciente</small>
                </div>

                <div class="mb-3">
                  <input type="number" class="form-control" v-model="paciente.telefono" id="telefono" name="telefono"
                    placeholder="Telefono" required />
                  <small id="helpId" class="form-text text-muted">Telefono del paciente</small>
                </div>
              </div>
            </div>
            <div class="datos_fechaNP">

              <div class="tituloNP">Fecha de Nacimiento</div>
              <div class="col1NP">
                <div class="mb-3">
                  <input type="text" class="form-control" v-model="paciente.fnac" id="fnac" name="fnac"
                    placeholder="Fecha de nacimiento" required />
                  <small id="helpId" class="form-text text-muted">Formato: DD/MM/AA</small>
                </div>
              </div>
            </div>
            <div class="datos_domicilioNP">

              <div class="tituloNP">Domicilio</div>
              <div class="col1NP">

                <div class="mb-3">
                  <input type="text" class="form-control" v-model="paciente.calle" id="calle" name="calle"
                    placeholder="Calle" required />
                  <small id="helpId" class="form-text text-muted">Calle</small>
                </div>


                <div class="mb-3">
                  <input type="text" class="form-control" v-model="paciente.localidad" id="localidad" name="localidad"
                    placeholder="Localidad" required />
                  <small id="helpId" class="form-text text-muted">Localidad</small>
                </div>

                <div class="mb-3">
                  <input type="text" class="form-control" v-model="paciente.provincia" id="provincia" name="provincia"
                    placeholder="Provincia" required />
                  <small id="helpId" class="form-text text-muted">Provincia</small>
                </div>
              </div>
            </div>

            <div class="menu-izqNP">
              <button type="submit" class="btn-acentoNP">Registrar</button>
              <RouterLink to="/listar-pacientes">
                <button type="button" class="btn-secondaryNP">Cancelar</button>
              </RouterLink>
            </div>

          </form>


        </div>
      </div>



    </div>
  </div>
</template>


<script>
export default {

  data() {
    return {
      paciente: {},
    };
  },
  methods: {
    async agregarRegistro() {
      console.log(this.tratamiento);

      var datosEnviar = {
        dni: this.paciente.dni,
        nombre: this.paciente.nombre,
        apellido: this.paciente.apellido,
        telefono: this.paciente.telefono,
        fnac: this.paciente.fnac,
        calle: this.paciente.calle,
        localidad: this.paciente.localidad,
        provincia: this.paciente.provincia
      };

      console.log(datosEnviar);

      await fetch("http://localhost:4000/api/pacientes", {
        method: "POST",
        body: JSON.stringify(datosEnviar),
        headers: {
          "Content-Type": "application/json",
        },
      })
        .then((res) => res.json())
        .catch((error) => console.error("Error", error))
        .then((response) => console.log("Success", response));

      alert("pacientes registrado");
      this.$router.push("/listar-pacientes");
    },
  },
};
</script>


<style>
* {
  margin: 0;
  padding: 0;
}


.flex-containerNP {
  display: flex;
  background-color: #2596be;
  flex-flow: row wrap;
  text-align: center;
}

.contenido-headerNP {

  background-color: #FAD8D6;
  width: 100%;
  height: 60px;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: space-between;
  align-content: center;
}

.mainNP {
    display: flex;
    flex-direction: row-reverse;
    justify-content: flex-end;
    width: 100%;
    background-size: cover;
    align-items: center;
}

.main-containerNP {
  width: 100%;
  display: flex;
  justify-content: space-between;
  flex-direction: column;

  margin-left: 150px;

}


.sidebarNP {
    background: #FAD8D6;
    width: 50px;
    height: 100vh;
    position: fixed;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.mainNP .main-containerNP .menu-izqNP a {
  display: flex;
  align-items: center;
  justify-content: center;

}

.menu-izqNP {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-content: center;
  align-items: center;
  text-align: center;
  margin-top: 50px;
}

.tituloNP {
  font-size: 30px;
  font-weight: 500;
  letter-spacing: 0.56px;
  margin-left: 64px;
  margin-top: 30px;
  text-align: initial;
}

.formularioNP {
  display: flex;
  flex-direction: column;

}

.datosNP{
  display: flex;
  flex-direction: row;
  margin-top: 30px;
  justify-content: space-between;
}

.datos_fechaNP .col1NP {
  display: flex;
  flex-direction: row;
  margin-top: 20px;
  margin-left: 92px;
}

.datos_domicilioNP .col1NP {
  display: flex;
    flex-direction: row;
    margin-top: 20px;
    margin-left: 92px;
    margin-right: 500px;
    justify-content: space-between;
}

.col1NP {

  display: flex;
  flex-direction: column;
  margin-left: 92px;
}

.col2NP {

  display: flex;
  flex-direction: column;
  margin-right: 600px
}

.contenido-headerNP nav ul {
  list-style: none;
  display: flex;
  margin-left: 70px;
  margin-top: 15px;

}

.contenido-headerNP .nav2 {
  display: flex;
  justify-content: space-between;
  align-items: center;

}

.contenido-headerNP nav ul li a {
  text-decoration: none;
  color: #00002E;
  margin: 0px 18px;
  font-weight: 500;
  font-size: 20px;
  line-height: 20px;
  letter-spacing: 0.1px;
}



.mainNP .btn-acentoNP {
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



.btn-secondaryNP {
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

.datosNP .btn-primary {
  font-size: 20px;
  text-transform: capitalize;
  height: 48px;
  width: 300px;
  border-radius: 30px;
  padding-left: 27px;
}

.datos_fechaNP .btn-primary {
  font-size: 20px;
  text-transform: capitalize;
  height: 48px;
  width: 89px;
  border-radius: 30px;
  padding-left: 27px;
  margin-right: 10px;
}

.datos_domicilioNP .btn-primary {
  font-size: 20px;
  text-transform: capitalize;
  height: 48px;
  width: 272px;
  border-radius: 30px;
  padding-left: 27px;
  margin-right: 70px;
}
.NP h1{
  
  font-size: 2rem;
    text-align: end;
    margin-right: 120px;
    margin-top: 10px;
}

</style>