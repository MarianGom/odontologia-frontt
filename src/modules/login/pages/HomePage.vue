<template>
 <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.1/css/all.min.css"
        integrity="sha512-MV7K8+y+gLIBoVD59lQIYicR65iaqukzvf/nwasF0nqhPay5w/9lJmVM2hMDcnK1OnMGCdVK+iQrJ7lzPJQd1w=="
        crossorigin="anonymous" referrerpolicy="no-referrer" />
<div class="flex-containerHP ">
        <div class="contenido-headerHP ">
            <nav class="nav">
                <ul id="linksHP ">
          
          <li><RouterLink to="/home-page">Inicio</RouterLink></li>
          <li><RouterLink to="/listar-pacientes">Pacientes</RouterLink></li>
          <li><RouterLink to="/listar-tratamientos">Tratamientos</RouterLink></li>
        </ul>
            </nav>
            <nav class="nav2">
                <div class="buscar">
                </div>
                <div class="icono-nav">
                </div>
            </nav>
        </div>
        <div class="sidebarHP ">
        </div>

        <section  class="mainHP ">   
            <div class="main-containerHP ">
                <div class="menu-izqHP ">
                 <RouterLink to="/listar-pacientes"> <button type="button" class="btn-acentoHP ">Pacientes</button></RouterLink>
                  <RouterLink to="/listar-tratamientos"><button type="button" class="btn-acentoHP ">Tratamientos</button></RouterLink>

                    <a class="btn-desabilitadoHP ">AGENDA</a>
                    <RouterLink to="/Login-Auth"><button type="button" class="btn-secondaryHP ">Cerrar Sesion</button></RouterLink>

                </div>
            </div>

        </section>
    </div>
</template>

<script>
export default {

}
</script>

<style>

.flex-containerHP {
    display: flex;
    background-color: #2596be;
    flex-flow: row wrap;
    text-align: center;
    height: auto;
}

.contenido-headerHP  {
     background-color: #FAD8D6;
        width: 100%;
        height: 60px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        align-content: center;
}

.mainHP  {
    display: flex;
    flex-direction: row-reverse;
    justify-content: flex-end;
    width: 100%;
    height: 100vh;
    background-size: cover;
    align-items: center;
}


.mainHP  .main-containerHP {
      
    width: 100%;
    display: flex;
    justify-content: space-around;
    align-content: flex-start;
    

}
.sidebarHP  {
    background: #FAD8D6;
    width: 50px;
    height: 100%;
    position: fixed;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.sidebarHP  a{

    display: flex;
    align-items: center;
    justify-content: center;
}
.mainHP  .main-containerHP  .menu-izqHP  a{

    display: flex;
    align-items: center;
    justify-content: center;
}

.mainHP  .menu-izqHP {
    display: flex;
    align-items: center;
    flex-direction: column;
   
}
.mainHP  .main-containerHP  .menu-derHP  a{

    display: flex;
    align-items: center;
    justify-content: center;
}


.mainHP  .menu-derHP {   
     display: flex;
    flex-direction: column;
    align-items: center;
    align-content: flex-start;
    justify-content: flex-end;
}

.contenido-headerHP  nav ul {
    list-style: none;
    display: flex;
    margin-left: 70px;
    margin-top:15px;
}
.contenido-headerHP  .nav2 {
      display: flex;
    justify-content: space-between;
    align-items: center;

}

.contenido-headerHP  nav ul li a {
    text-decoration: none;
    color: #00002E;
    margin: 0 12px;
    font-weight: 500;
    font-size: 20px;
    line-height: 20px;
    letter-spacing: 0.1px;

}

.btn-acentoHP  {
    font-style: normal;
    font-weight: 600;
    font-size: 48px;
    color: #FAD8D6;
    text-transform: uppercase;
    text-decoration: none;
    letter-spacing: 0.25px;
    background-color: #EE596D;
    width: 409px;
    height: 194px;
    border-radius: 40px;
    border: none;
    margin: 2% 0% 2% 0%;
    cursor: pointer;
    transition: all 1s ease;    
}


.mainHP  .btn-desabilitadoHP  {
    font-style: normal;
    font-weight: 600;
    font-size: 48px;
    color: #FAD8D6;
    text-transform: uppercase;
    text-decoration: none;
    background-color: #b6b6b6;
    width: 409px;
    height: 194px;
    border-radius: 40px;
    border: none;
    margin: 2% 0% 2% 0%;
    cursor: pointer;
    transition: all 1s ease;
}


.btn-secondaryHP  {
    font-style: normal;
    font-weight: 600;
    font-size: 30px;
    color: #00002E;
    text-transform: uppercase;
    text-decoration: none;
    background-color: #FAD8D6;
    width: 409px;
    height: 67px;
    border-radius: 40px;
    border: none;
    margin: 5% 0% 5% 0%;
    cursor: pointer;
    margin: 5% 0% 5% 0%;
    cursor: pointer;
    transition: all 1s ease;
}

.btn-primaryHP:hover {
  background-color: #00002E;
}
.btn-secondaryHP:hover {
  background-color: #9FF2F5;
}

.btn-acentoHP:hover {
  background-color: #847996;
}

</style>