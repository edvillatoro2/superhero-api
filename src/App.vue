<template>
  <div class="container">
    <h1>Superheros <span>&</span> villains Database</h1>
    <div class="list-table">
      <List />
    </div>
  </div>
</template>

<script>
import List from './components/List.vue';

export default {
  name: 'App',
  components: {
    List,
  }
}
</script>


<style scoped>
h1 {
  text-align: center;
  font-size: 3.8rem;
  color: rgba(16, 106, 134, 0.9);
  
}
span {
  font-size: 4.2rem;
  color: rgb(161, 62, 62);
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-weight: 700;
  text-shadow: 4px 4px 2px rgb(156, 145, 145, 0.8);
}

.container {
  margin: 0 25px;
}
@media only screen and (max-width: 860px) {
  .container {
    margin: 0 15px;
  }
}

.list-table {
    display: grid;
    grid-template-rows: 1fr;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 100px 1em;
}

@media only screen and (max-width: 860px) {
  .list-table {
    grid-template-columns: 1fr;
  }
}
</style>
