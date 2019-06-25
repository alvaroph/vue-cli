<template>
  <div>
    <v-img src="https://cdn.vuetifyjs.com/images/cards/desert.jpg" aspect-ratio="2.75"></v-img>


 <b-card
    :title="nombre"
    img-src="https://picsum.photos/600/300/?image=25"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="mb-2"
  >
    <b-card-text>
       <h3>Num PCs {{listaOrd.length}}</h3>
       
        <ul>
          <li v-for="(item, index) in listaOrd" v-bind:key="index">{{item.mac}}</li>
        </ul>
    </b-card-text>

    <b-button href="#" variant="primary">Más información</b-button>
  </b-card>
</div>

   
   
</template>

<script>
import Ordenador from './Ordenador.vue';

export default {
  name: 'AulasInformaticas',
  props: {
    nombre: String,
    listaOrd: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.aula {
  border: 1px solid black;
}
</style>
