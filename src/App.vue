<script setup>
import { computed, ref } from 'vue';
import ButtonCounter from './components/ButtonCounter.vue';
import BlogPost from './components/BlogPost.vue';
import PropsObjeto from './components/PropsObjeto.vue';
import PaginatePosts from './components/PaginatePosts.vue';
import LoadingSpinner from './components/LoadingSpinner.vue';
const posts = ref([
  // { title: 'Post 1', id: 1, body: 'Descripcion 1' },
  // { title: 'Post 2', id: 2, body: 'Descripcion 2' },
  // { title: 'Post 3', id: 3, body: 'Descripcion 3' },
  // { title: 'Post 4', id: 4, body: 'Descripcion 4' },
  // los eliminamos para usar datos que vienen de una API
]);
const postPage = 10;
const inicio = ref(0);
const fin = ref(postPage);
const loading = ref(true);
const favorito = ref('');
const cambiarFavorito = title => {
  favorito.value = title;
};
const next = () => {
  inicio.value += postPage;
  fin.value += postPage;
};

const previus = () => {
  inicio.value -= postPage;
  fin.value -= postPage;
};

fetch('https://jsonplaceholder.typicode.com/posts')
  .then(res => res.json())
  .then(data => (posts.value = data))
  .catch(e => console.log(e))
  .finally(() => {
    setTimeout(() => {
      loading.value = false;
    }, 2000);
  });

const max = computed(() => posts.value.length);
</script>

<template>
  <LoadingSpinner v-if="loading" />
  <div class="container" v-else>
    <h1>APP</h1>
    <ButtonCounter />
    <BlogPost title="Post 1" id="1" body="Descripcion 1" colorText="red" />
    <BlogPost title="Post 2" id="2" body="Descripcion 2" colorText="blue" />
    <BlogPost title="Post 3" id="3" body="Descripcion 3" colorText="orange" />
    <BlogPost title="Post 4" id="4" body="Descripcion 4" colorText="green" />

    <h1>Usar props como objetos</h1>
    <!-- <button @click="next">next Prueba</button>
  <button @click="previus">previus Prueba</button> -->
    <PaginatePosts
      @next="next"
      @previus="previus"
      :inicio="inicio"
      :fin="fin"
      :max="max"
    />
    <br />
    <PropsObjeto
      v-for="post in posts.slice(inicio, fin)"
      :key="post.id"
      :title="post.title"
      :id="post.id"
      :body="post.body"
      :favorito="cambiarFavorito"
    />
    <!-- ESTABA EN LINEA 34     @favorito="cambiarFavorito" -->
    <!-- puedo llamar al evento cono desee: favorito, mifavorito, reocrdar para escribirlo igual en el hijo -->

    <h2>Mi Post favorito</h2>
    <p>Es el : {{ favorito }}</p>
  </div>
</template>

<style scoped>
.red {
  color: red;
}
.blue {
  color: blue;
}
.green {
  color: green;
}
.orange {
  color: orange;
}
</style>
