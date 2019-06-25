<template>

 <b-card
    :title=computer.aula
    img-src="https://picsum.photos/600/300/?image=24"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="mb-2"
  >
    <b-card-text>

        <div>
            <div>{{ computer.nom }}</div>
            <div>{{ computer.mac }}</div>
        </div>
     </b-card-text>

    <b-button href="#" variant="primary">Més informació</b-button>
  </b-card>



</template>

<script>
export default {
  name: 'Ordenador',
  props: {
    computer: {},
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
.aula{
  border: 1px solid black;
}
</style>
