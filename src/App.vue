

<template>

  <div >
    
    <div id="cambioColores" style="width: 100vw; height: 100vh;">
    <div v-if="showBuscar" id="Titulo">
      <img src="./img/TituloPokemon.png" alt="">
    </div>
    

    <svg xmlns="http://www.w3.org/2000/svg" class="d-none">
                  <symbol id="exclamation-triangle-fill" viewBox="0 0 16 16">
                    <path d="M8.982 1.566a1.13 1.13 0 0 0-1.96 0L.165 13.233c-.457.778.091 1.767.98 1.767h13.713c.889 0 1.438-.99.98-1.767L8.982 1.566zM8 5c.535 0 .954.462.9.995l-.35 3.507a.552.552 0 0 1-1.1 0L7.1 5.995A.905.905 0 0 1 8 5zm.002 6a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>
                  </symbol>
                </svg>

           <div class="alert alert-danger d-flex align-items-center" role="alert"  v-if="alerta1" >
             <svg class="bi flex-shrink-0 me-2" role="img" aria-label="Danger:"><use xlink:href="#exclamation-triangle-fill"/></svg>
                <div>
                  Ingrese el nombre del pokemon  o el Id
                </div>
           </div>

        
           <svg xmlns="http://www.w3.org/2000/svg" class="d-none">
                  <symbol id="exclamation-triangle-fill" viewBox="0 0 16 16">
                    <path d="M8.982 1.566a1.13 1.13 0 0 0-1.96 0L.165 13.233c-.457.778.091 1.767.98 1.767h13.713c.889 0 1.438-.99.98-1.767L8.982 1.566zM8 5c.535 0 .954.462.9.995l-.35 3.507a.552.552 0 0 1-1.1 0L7.1 5.995A.905.905 0 0 1 8 5zm.002 6a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>
                  </symbol>
                </svg>

           <div class="alert alert-danger d-flex align-items-center" role="alert"  v-if="alerta2" >
             <svg class="bi flex-shrink-0 me-2" role="img" aria-label="Danger:"><use xlink:href="#exclamation-triangle-fill"/></svg>
                <div>
                 No existe el pokemon con el id:{{ id }}
                </div>
           </div>

 
      <div v-if="showBuscador" id="Buscador">
        <input type="search" name="" v-model="id"
         placeholder="Ingrese el Id del Pokémon o el Nombre"id="CaJadeTextodeBusquedaPokemon"  />
         <div >
           <button  id="boton" @click="Buscar" > <i class="fa fa-search" ></i></button>
         </div>
      </div>

     <div id="Contenedor">
    
  <div id="contenedorDatosPrincipales">
          <div id="Categoria">
            <h5 v-for="">{{ pokemonCategoria1 }}</h5>
            <h5>{{ pokemonCategoria2 }}</h5>
          </div>
          <div id="AlturaPeso">
          <p v-show="pokemonAltura"><b>Altura:</b> {{ pokemonAltura }}</p>
          <p v-show="pokemonPeso"><b>Peso:</b> {{ pokemonPeso }}</p><br><br><br>
      </div>
        <div v-show="pokemonId" id="idPokemon">
          <h4 >{{ "#" + pokemonId }}</h4>
        </div> 

      </div>
     
   
      <!--Informacion principak del pokemon -->
      
      <div id="contenedorPokemon">
      
          <img :src="img2Pokemon" alt="" />       
  <div>
          <h2>{{ pokemonName }}</h2>
         <!-- <div class="Sonido"> -->
          <!-- <q-circular-progress
            show-value
            font-size="60px"
            class="text-red q-ma-md"
            :value=100
            size="100px"
            :thickness="0.05"
            color="red"
            track-color="grey-3"
          >
            <q-icon name="volume_up"  @click="reproductor()"/>
        
          </q-circular-progress>
        </div> -->
        </div>
      </div>
 

    
      <div id="Habilidades">
        <!-- Habilidades del pokemon -->
       

        <div class="habilidad" v-show="estadisticaHabilidad1">
          <p >HP: </p>
            <q-circular-progress
              show-value
              font-size="20px"
              :value="estadisticaHabilidad1"
              size="100px"
              :thickness="0.22"
              color="teal"
              track-color="grey-3"
              class="q-ma-md"
            >
              {{ estadisticaHabilidad1 }}%
            </q-circular-progress>
         </div>
      
          <div class="habilidad" v-show="estadisticaHabilidad2">
          <p >ATTACK:</p>
            <q-circular-progress
              show-value
              font-size="20px"
              :value="estadisticaHabilidad2"
              size="100px"
              :thickness="0.22"
              color="teal"
              track-color="grey-3"
              class="q-ma-md"
            >
              {{ estadisticaHabilidad2 }}%
            </q-circular-progress>
        </div>
      
        <div class="habilidad" v-show="estadisticaHabilidad3">
  <p >DEFENSE:</p>
  <q-circular-progress
    show-value
    font-size="20px"
    :value="estadisticaHabilidad3"
    size="100px"
    :thickness="0.22"
    color="teal"
    track-color="grey-3"
    class="q-ma-md"
  >
    {{ estadisticaHabilidad3 }}%
  </q-circular-progress>
</div>

<div class="habilidad" v-show="estadisticaHabilidad4">
  <p >SPECIAL <br> ATTACK:</p>
  <q-circular-progress
    show-value
    font-size="20px"
    :value="estadisticaHabilidad4"
    size="100px"
    :thickness="0.22"
    color="teal"
    track-color="grey-3"
    class="q-ma-md"
  >
    {{ estadisticaHabilidad4 }}%
  </q-circular-progress>
</div>

      

       <div class="habilidad"v-show="estadisticaHabilidad5">
          <p >SPECIAL <br> DEFENSE:</p>
            <q-circular-progress
              show-value
              font-size="20px"
              :value="estadisticaHabilidad5"
              size="100px"
              :thickness="0.22"
              color="teal"
              track-color="grey-3"
              class="q-ma-md"
            >
              {{ estadisticaHabilidad5 }}%
            </q-circular-progress>
        </div>
       

       <div class="habilidad"v-show="estadisticaHabilidad6">
          <p >SPEED:</p>
            <q-circular-progress
              show-value
              font-size="20px"
              :value="estadisticaHabilidad6"
              size="100px"
              :thickness="0.22"
              color="teal"
              track-color="grey-3"
              class="q-ma-md"
            >
              {{ estadisticaHabilidad6 }}%
            </q-circular-progress>
          </div>
       


        <!-- <p>{{ pokemonHabilidad7 }}:</p> -->
      </div>
    </div>
    <div class="pie-chart"></div>
    <div v-if="showBuscar" id="Buscar">
      <button @click="BuscarPokemon">BUSCAR</button>
    </div>
  </div>
</div>


</template>

<script setup>
import axios from "axios";
import { ref } from "vue";

// let imgPokemon = ref("")
let img2Pokemon = ref("");
let id = ref("");
let pokemonId = ref("");
let pokemonName = ref("");
let pokemonAltura = ref("");
let pokemonPeso = ref("");
let pokemonCategoria1 = ref("");
let pokemonCategoria2 = ref("");
let estadisticaHabilidad1 = ref("");
let estadisticaHabilidad2 = ref("");
let estadisticaHabilidad3 = ref("");
let estadisticaHabilidad4 = ref("");
let estadisticaHabilidad5 = ref("");
let estadisticaHabilidad6 = ref("");
let  showBuscador = ref(false);
let showBuscar =ref(true);
let alerta1 = ref("");
let alerta2 = ref("");


function BuscarPokemon(){
  showBuscador.value= !showBuscador.value
}

async function Buscar() {
  if(alert()){
    return;
  }
  showBuscar.value= false
  // alert("You clicked the button!");
  
  let Pokemon = await axios.get(
    `https://pokeapi.co/api/v2/pokemon/${id.value}`
  );
  img2Pokemon.value =
    Pokemon.data.sprites.other["official-artwork"].front_default;
  console.log(Pokemon.data.sprites.other["official-artwork"].front_default);

  pokemonId.value = Pokemon.data.id;
  console.log(Pokemon.data.id);

  pokemonName.value = Pokemon.data.species.name;
  console.log(Pokemon.data.species.name);

  pokemonAltura.value = Pokemon.data.height;
  console.log(Pokemon.data.height);

  pokemonPeso.value = Pokemon.data.weight;
  console.log(Pokemon.data.weight);

  if (Pokemon.data.types["0"]) {
    pokemonCategoria1.value = Pokemon.data.types["0"].type.name;
    console.log(Pokemon.data.types["0"].type.name);
  }
  if (Pokemon.data.types["0"] && Pokemon.data.types["1"]) {
    pokemonCategoria1.value = Pokemon.data.types["0"].type.name;
    console.log(Pokemon.data.types["0"].type.name);
    pokemonCategoria2.value = Pokemon.data.types["1"].type.name;
    console.log(Pokemon.data.types["1"].type.name);
  }

  
  estadisticaHabilidad1.value = Pokemon.data.stats[0].base_stat;
  estadisticaHabilidad2.value = Pokemon.data.stats[1].base_stat;
  estadisticaHabilidad3.value = Pokemon.data.stats[2].base_stat;
  estadisticaHabilidad4.value = Pokemon.data.stats[3].base_stat;
  estadisticaHabilidad5.value = Pokemon.data.stats[4].base_stat;
  estadisticaHabilidad6.value = Pokemon.data.stats[5].base_stat;


  // pokemonSonido.value = Pokemon.data.cries.legacy
CategoriaxColorcomparacion()
buscadorXcategoria()


} 

 async function reproductor() {
      let Pokemon = await axios.get(`https://pokeapi.co/api/v2/pokemon/${id.value}` );
   const pokemonSonido = Pokemon.data.cries.latest;
    console.log(Pokemon.data.cries.latest);

    const audio = new Audio(pokemonSonido);
    audio.play();
  }

  let CategoriaxColor ={
    normal: "#A8A878",
    fire: "#F08030",
    water: "#6890F0",
    electric: "#F8D030",
    grass: "#78C850",
    ice: "#98D8D8",
    fighting: "#C03028",
    poison: "#A040A0",
    ground: "#E0C068",
    flying: "#A890F0",
    psychic: "#F85888",
    bug: "#A8B820",
    rock: "#B8A038",
    ghost: "#705898",
    dragon: "#7038F8",
    dark: "#705848",
    steel: "#B8B8D0",
    fairy: "#EE99AC",
  }
  function CategoriaxColorcomparacion(){
    let color= CategoriaxColor[pokemonCategoria1.value]
    cambioColores.style.backgroundColor=color
  }
  let buscadorXcategorias={
    normal: "#000000",
    fire: "#3060F0",
    water: "#F06830",
    electric: "#3040A8",
    grass: "#FF5733",
    ice: "#E6E6FA",
    fighting: " #000000",
    poison: "#444444",
    ground: "#555555",
    flying: "#ADD8E6",
    psychic: "#000000",
    bug: "#000000",
    rock: "#382FB8",
    ghost: "#000000",
    dragon: "#F8B838",
    dark: "#000000",
    steel: "#000000",
    fairy: "#000000",
  }
  function buscadorXcategoria(){
    let color= buscadorXcategorias[pokemonCategoria1.value]
    boton.style.backgroundColor=color;
    // input.style.outlineColor=color;
    CaJadeTextodeBusquedaPokemon.style.outlineColor = color;
    // #Buscador input{
//   border-radius: 20px;
//   height: 40px;
//   width: 30%;
//   position: relative;
//   left: 1.5%;
//   font-size: 20px;

// /* border-bottom: 3px solid red; */
// /* border-color: blue; */
// outline-color:red; 
// }
  }
  


  function alert(){
    // var id = document.getElementById("id");
    if(id.value === "" || id.value == 0){
      alerta1.value = true;
      setTimeout(()=>{
        alerta1.value = false;
      },3000)
      return true
    }
    return false

  }
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
  box-sizing: 0px;
}
body{
  background-image: url(./src/img/pokemon.png);
  background-size: 100% 100vh;
  background-repeat: no-repeat;
}

.bi {
  width: 5%;
}
.alert{
  width: 60%;
  height: 10%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 2%;
  position: fixed;  
  left: 50%;
  /* top: 2%; */
  transform: translate(-50%);
  z-index: 1000;
  font-family: cursive;
  font-weight: 900;
  font-size: 20px;
}

#Titulo img{
margin-left: 65%;
  width: 30%;

}
#Buscar button{
  display: flex;
  position: fixed;
  left: 85%;
  top: 90%;  
  transform: translate(-50%, -50%);
  margin-right: 50PX;
    /* margin-top: 6em; */
  background-color: rgb(34, 47, 233);
  font-size: 40px;
  /* padding:1%; */
  padding-left: 1%;
  padding-right: 1%;
  border-radius: 20px;
  font-weight: 1000;
  font-family: letra2;
}

#Buscador{
  display: flex;
  justify-content: center;
  text-align: center;
  align-items: center;
  /* margin-left: 15%; */
  padding-top: 2%;
  width:100%;
}
#Buscador input{
  border-radius: 20px;
  height: 40px;
  width: 30%;
  position: relative;
  left: 1.5%;
  font-size: 20px;

/* border-bottom: 3px solid red; */
/* border-color: blue; */
outline-color:red; 
}

/* #Buscador input:hover {
  border: 2px solid rgb(15, 192, 228);
  cursor: pointer;
} */

#boton{
  border-radius: 50px;
  width: 40px;
  height: 40px;
  background-color: red;
  outline: none;
border: none;
position: relative;
right: 55%;
  transition: .5s;
}
#boton i{
  color: white;
  transition: all .7 ease;
}

#boton:hover i{
  transform: rotate(-555deg)
}

#contenedorPokemon {
  justify-content: center;
  text-align: center;
  align-items: center;
}
#contenedorPokemon h2{
  text-transform: uppercase;
  font-family: letra2;
   font-weight: 900;
   text-align: center;
   font-size: 90px;
  
   /* text-transform:lowercase; */
}
#contenedorDatosPrincipales p {
  /* background-color: black; */
  font-size: 30px;
  justify-content: center;
  text-align: center;
  margin: 0;
  padding: 0px;
}

#idPokemon{
  bottom: 350px;
 z-index: -100;
  font-family:letra4;
}

#idPokemon h4{
  font-size: 150px; 
  z-index: -100;
  text-align: center;
}
#AlturaPeso{
  font-family: letra1;
}

#Contenedor {
 display: grid;
 grid-template-columns: repeat(3,1fr);
  margin-top: 1%;
  /* margin-bottom: 30%; */
  align-items: center; 
  /* margin-bottom: 2%; */
  margin-left: auto;
  margin-right: auto;
  justify-content: center;
  width: 90%;
}

#Habilidades{
  display: grid;
  grid-template-columns: repeat(3,1fr);
  grid-gap: 20px;
  width: 100%;
}
.habilidad{
  display: grid;
  justify-content: center;
  justify-items: center;
  align-items: center;
  font-family: letra1; 
   font-size: 25px;
}
.habilidad p {
  padding: 0px;
  margin: 0;
line-height: 4vh;
 
}

#Categoria {
  display: flex;
  gap: 30px;
  justify-content: center;
  text-transform: capitalize;

}
#Categoria h5{
    font-weight: 900;
    font-family: letra5;
}


#tituloPokemon h3{
   font-family: tatis;
  font-size: 80px;
}




@font-face {
  font-family: letra;
  src: url("./MorningSpirit.ttf");
}
@font-face {
  font-family: letra1;
  src: url("./GummyBear.ttf");
}

@font-face {
  font-family: letra2;
  src: url("./Heyam.ttf");
}
@font-face {
  font-family: letra3;
  src: url("./le.ttf");
}
@font-face {
  font-family: letra4;
  src: url("./fFaseBulan.ttf");
}
@font-face {
  font-family: letra5;
  src: url("./LittleGroovyDemoRegular.ttf");
}
@media screen and (max-width:425px){
  
.alert{
  width: 80%;
  text-align: center;

}
.bi{
  width: 10%;
}
#Buscador input{
  width: 70%;
}
#Buscar button{
  position: fixed;
  left: 75%;
}
#Titulo img{
margin-left: 10%;
  width: 80%;

}
#Contenedor {
 display: grid;
 grid-template-columns: repeat(1,1fr);
 width: 100%;
 margin-top: 10%;

}
#contenedorPokemon h2{
  font-size: 60px;
}
#contenedorPokemon img{
  width: 90%;
}
#Habilidades{
  display: grid;
  grid-template-columns: repeat(2,1fr);
}
}
@media screen and (max-width:800px) and (min-width:500px){
  /* #Contenedor {
 display: grid;
 grid-template-columns: repeat(2,1fr);
 width: 100%;
justify-content: center;
} */
  #Habilidades{
   position: relative;
   left: 30%;
   top:5%;
   transition: transform(-50% -50%);

    
  } 
  #contenedorPokemon{
   position: relative;
   right: 30%;
  }
  #contenedorDatosPrincipales{
    position: relative;
   right: 10%;
  }
#Contenedor {
grid-template-columns: repeat(2, 1fr);


 }
.bi{
  width: 10%;
}
#contenedorPokemon h2{
  font-size: 60px;
}
#contenedorPokemon img{
  width: 90%;
}
}
  @media screen and (max-width:1840px) and (min-width:2440px){
    #cambioColores{
      height:1000vh;
  }
    #Contenedor{
      padding-botton:5%;
  }

</style>
