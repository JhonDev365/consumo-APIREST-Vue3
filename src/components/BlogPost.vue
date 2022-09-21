<script setup>
const props = defineProps(['title', 'id', 'body', 'colorText']);
//los peudo usar accediento a props.title
</script>

<template>
  <!-- <section>
    <div>
      <h1 :class="`${colorText}`">{{ title }}</h1>
      <h1 :class="colorText">{{ title }}</h1>
      <p>{{ id }} {{ body }}</p>
    </div>
  </section> -->
  <div class="card">
    <div class="card-body">
      <h5 :class="colorText">{{ title }}</h5>
      <p>{{ id }} {{ body }}</p>
    </div>
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
