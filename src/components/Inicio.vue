<template>
<div>


<b-container>


  <b-row>
    <div v-for="(item,index) in aulas" :key="item"  cols="4">
        <AulasInformaticas :listaOrd="ordenadoresAulas(item)" :nombre="item"></AulasInformaticas>
    </div>
  </b-row>
</b-container>
   
       
    





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
