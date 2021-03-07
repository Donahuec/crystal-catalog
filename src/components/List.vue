<template>
  <div class="List">
    <h1>{{ msg }}</h1>
    <div class="row" :v-if="info != null">
        <div v-for="spec in info.items" :key="spec.id">
          <Specimen :specimen="spec.data"></Specimen>
        </div>
    </div>
  </div>
</template>

<script>
import Specimen from './Specimen.vue';

export default {
  name: 'List',
  props: {
    msg: String
  },
  components: {
    Specimen
  },
  data() {
    return {
      info: []
    }
  },
  methods: {
    fetchItems () {
      fetch(process.env.VUE_APP_API_ROOT + "specimen?$orderby=data/Title/iv",
      {
        headers: 
        {
          'Authorization': process.env.VUE_APP_API_KEY,
          'X-Flatten': 'true'
        }
      }
      )
        .then(response => response.json())
        .then(data => this.info = data)
    }
  },
  mounted() {
    this.fetchItems();
  }
}
</script>