<template>
<div>


<div class="overflow-auto">
    <b-pagination
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
      aria-controls="my-table"
    ></b-pagination>

    <p class="mt-3">Current Page: {{ currentPage }}</p>

    <b-table
      id="my-table"
      :items="computers"
      :per-page="perPage"
      :current-page="currentPage"
      small
    ></b-table>
  </div>

   <div v-for="(item,index) in aulas" :key="item" lg3 xl3>
        <AulasInformaticas :listaOrd="ordenadoresAulas(item)" :nombre="item"></AulasInformaticas>
      </div>






       <div v-for="(item) in computers" :key="item.mac">
      <Ordenador :computer="item"></Ordenador>
    </div>

    </div>
 
</template>

<script>
import AulasInformaticas from './AulasInformaticas.vue';
import Ordenador from './Ordenador.vue';

export default {
  name: 'inicio',
  data() {
    return {
      computers: [],
      aulas: [],
      perPage: 10,
      currentPage: 1
    };
  },
  components: {
    Ordenador,
    AulasInformaticas,
  },

  mounted() {
    this.obtenDatos();
  },
  computed: {
      rows() {
        return this.computers.length
      }
    },
  methods: {
    ordenadoresAulas(a) {
      return this.computers.filter(pc => pc.aula === a);
    },
    obtenDatos() {
      return fetch('http://labs.iam.cat/api/api.php/records/equips?size=100')
        .then(response => response.json())
        .then(response => response.records)
        .then((response) => {
          this.computers = response;
          this.aulas = [...new Set(response.map(x => x.aula))];
        });
    },
  },
};
</script>
