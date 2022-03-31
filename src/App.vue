<script>
//<script setup>
//import HelloWorld from './components/HelloWorld.vue'
//import TheWelcome from './components/TheWelcome.vue'
  let id = 0

  export default {
    data() {
      return {
        titulo: "Kitties & Doggos",
        mainImg: true,
        newAnimal: '',
        divID: "head",
        animals: [
          {id: id++, text: "Puppies"},
          {id: id++, text: "Kitties"}
        ]
      }
    },
    methods: {
      toggle(){
        this.mainImg = !this.mainImg
      },
      addAnimal(){
        this.animals.push({ id: id++, text: this.newAnimal })
        this.newAnimal = ''
      },
      removeAnimal(animal){
        this.animals = this.animals.filter((a) => a !== animal)
      }
    },
  }
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div id="head" class="container-fluid">
      <a class="navbar-brand" href="#">{{titulo}}</a>
      <div class="navbar-nav">
        <a class="nav-link active" aria-current="page" href="#Home">Home</a>
        <a class="nav-link" href="#List">Listing</a>
      </div>
    </div>
  </nav>
  <header>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    
  <!--
    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  -->
  </header>
  
  <main>
    <!--<TheWelcome />-->
    <div :id="divID">
      <!--<img alt="Vue logo" class="logo" src="./assets/puppy.png" width="70" height="70" />-->
      <h1>{{titulo}}</h1>
    </div>
    <a name="Home"></a>
    <div v-if="mainImg">
      <div class="card" style="width: 25rem;">
        <img alt="Imagen perrito" src="./assets/mascota1.jpg" class="card-img-top" height="300"/>
        <div class="card-body">
          <h5 class="card-title">Puppy</h5>
          <p class="card-text">The puppy is happy to see you</p>
        </div>
      </div>
    </div>
    <div v-else>
      <div class="card" style="width: 25rem;">
        <img alt="Imagen perrito" src="./assets/mascota2.jpg" class="card-img-top" height="300"/>
        <div class="card-body">
          <h5 class="card-title">Kitty</h5>
          <p class="card-text">The kitty is nervous, but still likes you</p>
        </div>
      </div>
    </div>
    <button @click="toggle" class="btn btn-success"> Change </button>

    <div id="carouselSlides" class="carousel slide" data-bs-ride="carousel">
      <ol class="carousel-indicators">
        <li data-target="#carouselSlides" data-slide-to="0" class="active"></li>
        <li data-target="#carouselSlides" data-slide-to="1"></li>
      </ol>
      <div class="carousel-inner">
        <div class="carousel-item active">
          <img src="./assets/mascota3.jpg" class="d-block w-100" alt="perrito">
        </div>
        <div class="carousel-item">
          <img src="./assets/mascota4.jpg" class="d-block w-100" alt="gatito">
        </div>
      </div>
      <button href="#carouselSlides" class="carousel-control-prev" type="button"  data-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button href="#carouselSlides" class="carousel-control-next" type="button"  data-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
    
    <div>
    <a name="List"></a>
      <div>
        <h3>¿Other animals you'd like to see?</h3>
        <form @submit.prevent="addAnimal">
          <input v-model="newAnimal">
          <button class="btn btn-success">Add</button>
        </form>
      </div>
      <div class="card" style="width: 25rem;">
        <ul class="list-group list-group-flush">
          <li class="list-group-item" v-for="animal in animals" :key="animal.id">{{animal.text}}
            <button class="btn btn-danger" @click="removeAnimal(animal)">X</button>
          </li>
        </ul>
      </div>
    </div>
  </main>
</template>

<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

div{
  margin: 10px 20px 20px 10px;
}

.head{
  margin: 0 auto;
  display: flex;
  flex-flow: row wrap;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  /*body {
    display: flex;
    align-content: center;
  }*/

  /*#app {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 0 2rem;
  }*/
  
  main{
    display:flex;
    max-width: 50%;
    flex-flow: column nowrap;
    align-content: center;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
