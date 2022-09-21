<template>
  <!-- <section>
    <div>
      <h1>{{ title }}</h1>
      <p>{{ id }} {{ body }}</p>

      <button @click="favorito(title)">Favorito</button>
    </div>
  </section> -->
  <div class="card mb-3">
    <div class="card-body">
      <h5>{{ title }}</h5>
      <p>{{ id }} {{ body }}</p>
      <!-- //usamos $emit(''), para emitir al padre este eventos, metodo como segundo argumento  -->
      <!-- <button @click="$emit('favorito', title)">Favorito</button> -->
      <!-- ahora usando defineEmit podemos acceder al que nosotros estamos especificanso
        ademas que ya no usamos el  $  -->
      <!-- <button @click="emit('favorito', title)">Favorito</button> -->
      <!-- tambien podemos pasrale por medio de props la funcion -->
      <button @click="favorito(title)" class="btn btn-outline-primary">
        Favorito
      </button>
    </div>
  </div>
</template>

<script setup>
//este objeto sera bien dinamico
defineProps({
  title: String,
  id: Number,
  body: {
    type: String,
    default: 'Sin Descripcion',
  },
  favorito: Function,
});
//usando defineemits
// const emit = defineEmits(['favorito']);
</script>
