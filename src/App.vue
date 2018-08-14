<template>
  <div id="app">
    <b-container fluid>
      <b-col md="6" class="my-1">
        <b-form-group horizontal label="Filter" class="mb-0">
          <b-input-group>
            <b-form-input v-model="filter" placeholder="Type to Search" />
            <b-input-group-append>
              <b-btn :disabled="!filter" @click="filter = ''">Clear</b-btn>
            </b-input-group-append>
          </b-input-group>
        </b-form-group>
      </b-col>
    <b-table striped hover :sort-by.sync="sortBy" :sort-desc.sync="sortDesc" :items="jobs" :fields="fields" :filter="filter" @filtered="onFiltered"></b-table>
    {{ jobs.length }}
    <p>
      Sorting By: <b>{{ sortBy }}</b>,
      Sort Direction: <b>{{ sortDesc ? 'Descending' : 'Ascending' }}</b>
    </p>
    </b-container>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import jobs from './my_file.json'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  name: 'app',
  components: {
    HelloWorld
  },
  data(){
    return{
      sortBy: 'age',
      sortDesc: false,
      filter: null,
      fields: [
        { key: 'jobName', sortable: true },
        { key: 'jobPublicationDate', sortable: true },
        { key: 'jobEmployer', sortable: true },
        { key: 'jobLocation', sortable: true },
        { key: 'jobStartDate', sortable: true }
      ],
      jobs: jobs.jobs
    }
  },
  methods: {
    onFiltered (filteredItems) {
      // Trigger pagination to update the number of buttons/pages due to filtering
      this.totalRows = filteredItems.length
      this.currentPage = 1
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
