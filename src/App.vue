
<script setup>
import { onMounted, ref } from "vue";
import Block from "@/components/Block.vue";
import Results from "./components/Results.vue";

const isPlaying = ref(false);
const delay = ref(null);
const score = ref(null);
const showResults= ref(false)

const start = () => {
  delay.value = 2000 + Math.random() * 5000;
  isPlaying.value = true;
  console.log(delay);
};

const endGame = (reactionTime) => {
  score.value=  reactionTime;
  isPlaying.value = false; 
  showResults.value= true;
}
</script>

<template>
  <div class="game">
    <h1>Meraj Reaction time</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" :key="delay" />
    <!-- <p v-if="showResults">Reaction time {{score}} ms</p> -->
     <Results v-if="showResults" :score="score"/>
  </div>
</template>
<style>
h1 {
  margin: 50px 0;
}
.game {
  text-align: center;
  display: flex;
  flex-direction: column;
}
button {
  padding: 10px 20px;
}
</style>

<!-- 
<script setup>
import { ref, reactive, computed } from 'vue';
import Modal from "@/components/Modal.vue"

const title= ref("My first Vue App")

const showModal= ref(false)

const toggleModal = () => {
  showModal.value= !showModal.value
}

const books = reactive([
  {title:'name of the wind', author:'Meraj Naqui', img:"src/assets/1.jpg", isFav: true},
  {title:'name of the rain', author:'Baba Naqui', img:"src/assets/2.jpg", isFav: false},
  {title:'name of the water', author:'Papa Naqui', img:"src/assets/3.jpg", isFav: true}
  ])

const url="https://meraj-three.vercel.app/";

const togglefav = (book) => {
  book.isFav=!book.isFav
}

const passData= reactive({
  title : "My first vue App",
  header : "Singup for Giveaway",
  text : "Grab for ninja swag for half price"
  
})

const filteredBooks = computed(() => {
 return books.filter((book)=>book.isFav)
  
})


</script>

<template>
  <h1>{{title}}</h1>
  <div v-if="showModal">
  <Modal :header="passData.header" :text="passData.text" theme="sale"  @close="toggleModal"/> 
</div>
<button @click="toggleModal">Open Modal</button>
  <div>
    
   <ul>
    <li v-for="book, index in filteredBooks" :key="index" :class="{fav: book.isFav}" @click="togglefav(book)">
      <img :src="book.img" :alt="book.img" width="75" height="auto"/>
      <h3>Title : {{book.title}}</h3>
      <p>Author : {{ book.author }}</p>  
</li>
</ul>
<div>
  <button @click="toggleShowBooks">
    <span v-if="showBooks">Hide Books</span>
    <span v-else>Show Books</span>
   <span v-if="!showBooks">Show Books</span> 
  </button>
  <div v-show="showBooks">Currently showing book</div>
 <button @click="age++">increase age </button>
<button v-on:click="age--">Decrease age</button>
<button @click="changeTitle('Hight to the Sky')">Change the title</button>
</div>
  </div>
</template>


<style>
body{
  background: #eee;
  width: 960px;
  margin: 20px auto;
  padding: 0;


}
.box{
  margin:0;
  padding: 0;
 
}
ul{
  display: flex;
  flex-direction: column;
  width: 850px;
}
 li {
  margin:0;
  padding:0;
  width:100%
}
li{
  list-style: none;
  background: #fff;
  margin: 20px auto;
  padding: 10px 20px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;

}
li.fav{
  background: #ff9ed2;
  color:#fff;
  cursor: pointer;
}
h3{
  text-transform: uppercase;

}


</style> -->
