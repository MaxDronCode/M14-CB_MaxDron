<script setup>
import { ref, reactive } from 'vue'

const contador = ref(0) // <- Per guardar valors, els guarda 'com a objecte', per això hi accedim a través del seu atribut .value
const incrementar = () => {
  contador.value++
}
const usuari = reactive({ // <- Per renderitzar un objecte, s'ha de fer amb 'reactive'. Pots accedir directament a les seves propietats
  nom: "Pepe",
  edat: 87
})
const augmentarEdat = () => {
  usuari.edat++
}

// variables a les quals els atributs d'un tag html accedeixen utilitzant la directiva 'v-bind' o be ':' que es la sintaxis abreviada
const titol = "Text que apareix" 
const imatgeUrl = 'https://cdn.pixabay.com/photo/2023/06/14/23/12/sunset-8064078_1280.jpg'

// Variabe que modifiquem amb v-model
const nomUsuari = ref('')

// Exemple de v-for
const productos = [{
  id: 1,
  nomProd: "Manzana",
  preu: 1.25
},
{
  id: 2,
  nomProd: "Pera",
  preu: 2.25
},
{
  id: 3,
  nomProd: "Platano",
  preu: 3.34
}]

// Exemple v-if / v-else
const logat = ref(false)
const valorBoto = ref('Logarse')
const logarse = () => {
  logat.value = !logat.value
  valorBoto.value = logat.value ? 'Deslogarse' : 'Logarse'
}

// Exemple v-show
const mostrar = ref(false)

// Exemple v-on
</script>

<template>
  <main>
    <section class="container">
      <h2>Exemple REF</h2>
      <h4>El Comptador es: <span>{{ contador }}</span></h4>
      <br />
      <button @click="incrementar">Incrementar</button>
    </section>
    <section class="container">
      <h2>Exemple REACTIVE</h2>
      <h4>Nom Usuari: <span>{{ usuari.nom }}</span></h4>
      <h4>Edat usuari: <span>{{ usuari.edat }}</span></h4>
      <br>
      <button @click="augmentarEdat">Augmentar Edat</button>
    </section>
    <section class="container">
      <h2>Exemple V-Bind</h2>
      <h4 v-bind:title="titol"> Passa el ratolí per sobre</h4>
      <img :src="imatgeUrl" alt="imatge de prova">
    </section>
    <section class="container">
      <h2>Exemple V-Model</h2>
      <h4>Nom Usuari: <span>{{ nomUsuari }}</span></h4>
      <input type="text" v-model="nomUsuari" placeholder="Pepe, Manel...">
    </section>
    <section class="container">
      <h2>Exemple V-For</h2>
      <div style="display: flex; justify-content: space-between;">
        <ul>
          <li v-for="producto in productos" :key="producto.id">{{ producto.nomProd }}</li>
        </ul>
        <ul>
          <li v-for="producto in productos" :key="producto.id"><span>{{ producto.preu }}€</span></li>
        </ul>
      </div>
    </section>
    <section class="container">
      <h2>Exemple v-if / v-else</h2>
      <h4 v-if="logat">Benvingut a la aplicació</h4>
      <h4 v-else>Siusplau inicia sessió</h4>
      <button @click="logarse">{{ valorBoto }}</button>
    </section>
    <section class="container">
      <h2>Exemple v-show</h2>
      <button @click="mostrar = !mostrar">Mostrar</button>  
      <span><h4 v-show="mostrar">Text que es mostra</h4></span>
    </section>
    <section class="container">
      <h2>Exemple v-on</h2>
      <h4>Ja l'hem fet</h4>
    </section>
  </main>
</template>

<style scoped>
.container{
  border: 1px solid #ffffff88;
  border-radius: 8px;
  margin: 10px;
  padding: 10px;
  box-shadow: 0 0 45px 1px #ffffff17;
}
button{
  padding: 10px;
  background-color: #333;
  color: #fff;
  border-radius: 5px;
  font-size: 16px;
  margin: 10px;

  &:hover{
    background-color: #555;
  }
}
ul{
  list-style: circle;
}
span, h2{
  color: #fff;
}
h4{
  font-size: 16px;
}
img{
  width: 400px;
  height: auto;
}
input[type="text"] {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  font-family: 'Arial', sans-serif;
  background-color: #f8f8f8;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
}

input[type="text"]:focus {
  border-color: #007bff;
  box-shadow: 0 0 8px rgba(0, 123, 255, 0.5);
  outline: none;
}

input[type="text"]::placeholder {
  color: #999;
  font-style: italic;
}

</style>
