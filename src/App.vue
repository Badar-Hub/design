<template>
  <Header class="q-py-md text-white" />
  <div class="grid-row full-width">
    <Card />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Card from './components/Card.vue';

export default {
  name: 'App',
  components: {
    Header,
    Card,
  },
};
</script>

<style>
body {
  background-color: #f1f1f1;
}
.grid-row {
    display: grid;
    padding: 3px;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
}
</style>
