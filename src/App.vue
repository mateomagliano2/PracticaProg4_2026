<script setup>
import BlogPost from './components/BlogPost.vue';
import { ref } from 'vue';
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
</script>


<template>

  <div class="container">
    <h1>Hola Maquina</h1>
    <h2>{{ favorito }}</h2>
    <BlogPost v-for="post in posts" :key="post.id" :title="post.title" :id="post.id" :body="post.body" class="mb-2"
      @CambiarFavoritoNombre=cambiarFavorito />
  </div>

</template>
