<template>

  <section class="src-components-tabla">
    <div class="container-fluid mt-3">
      <div class="jumbotron">

        <div v-if="personas.length" class="table-responsive"> 
          <table class="table table-dark align-middle align-self-center">
              <tr> 
                  <th>Indice</th>
                  <th>Nombre</th>
                  <th>Edad</th>
                  <th>Mail</th>
              </tr>
              <tr v-for="(personas, index) in personas" :key="index"> 
                  <td>{{index + 1}}</td>
                  <td>{{personas.Nombre}}</td>
                  <td>{{personas.Edad}}</td>
                  <td>{{personas.Mail}}</td>
              </tr>
          </table>
        </div>
        <h4 v-else class="alert alert-danger text-center">No se encontraron personas en MockApi</h4>

      </div>
    </div>
  </section>

</template>

<script>

import axios from 'axios'

  export default  {
    name: 'src-components-tabla',
    props: [],
    mounted () {
      this.getPostMockApi()
    },
    data () {
      return {
         url: 'https://62856fea96bccbf32d62d26c.mockapi.io/TP7',
        personas: []
      }
    },
    methods: {
    async getPostMockApi() {
        try {
          let { data } = await axios(this.url)
          this.personas = data
        } catch (error) {
          console.error('Error Axios', error);
        }
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-tabla {
  }
  .jumbotron {
    background-color: rgb(64, 210, 255);
  }

</style>
