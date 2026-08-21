<script setup>
import BlogPost from './components/BlogPost.vue';
import { ref } from 'vue';
import PaginatePost from './components/PaginatePost.vue';
// const posts = ref([
//   { id: 1, title: 'Post 1', body: 'RIVER' },
//   { id: 2, title: 'Post 2', body: 'RIVER 1' },
//   { id: 3, title: 'Post 3', body: 'Murieron en el 2018' },
//   { id: 4, title: 'Post 4' }
// ]);
const posts = ref([])
fetch('https://jsonplaceholder.typicode.com/posts')
  .then(response => response.json())
  .then(data => posts.value = data)


const favorito = ref('');
const cambiarFavorito = (title) => {
  favorito.value = title;
}

const inicio = ref(0);
const fin = ref(pageXpost);
const pageXpost = 5;
const next = () => {
  inicio.value = inicio.value + pageXpost;
  fin.value = fin.value + pageXpost;
}
const prev = () => {
  inicio.value = inicio.value - pageXpost;
  fin.value = fin.value - pageXpost;
}
</script>


<template>

  <div class="container">
    <h1>Hola Maquina</h1>
    <PaginatePost class="mb-2" @next="next" @prev="prev" />
    <hr>
    <h2>{{ favorito || "Ninguno" }}</h2>
    <button class="btn btn-outline-primary" @click="prev">Prev</button>
    <button class="btn btn-outline-primary" @click="next">Next</button>
    <hr>
    <BlogPost v-for="post in posts.slice(inicio, fin)" :key="post.id" :title="post.title" :id="post.id"
      :body="post.body" class="mb-2" @CambiarFavoritoNombre=cambiarFavorito />
  </div>

</template>
