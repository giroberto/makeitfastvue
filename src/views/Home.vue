<template>
    <div>
        <b-row>
            <b-col md="6" class="my-1">
                <b-form-group horizontal label="Filter" class="mb-0">
                    <b-input-group>
                        <b-form-input v-model="filter" placeholder="Type to Search" />
                    </b-input-group>
                </b-form-group>
            </b-col>
        </b-row>
        <b-table 
            hover 
            :items="jobs" 
            :fields="fields" 
            :filter="filter" 
            show-empty
            stacked="md"
            @filtered="onFiltered"
            @row-clicked="showDetails">
        <span slot="jobLocation" slot-scope="jobs" v-html="jobs.value">     
        </span>
        </b-table>
    </div>
</template>

<script>
import jobs from "@/my_file.json";
export default {
  data() {
    return {
      modalInfo: { jobName: "", content: "" },
      jobs: jobs.jobs,
      sortBy: 'jobPublicationDate',
      sortDesc: true,
      fields: [
        { key: "jobName", sortable: true},
        { key: "jobPublicationDate", sortable: true},
        { key: "jobEmployer", sortable: true},
        { key: "jobLocation", sortable: true}
      ],
      filter: null
    };
  },
  methods: {
    onFiltered(filteredItems) {
      // Trigger pagination to update the number of buttons/pages due to filtering
      this.totalRows = filteredItems.length;
      this.currentPage = 1;
    },
    showDetails(record, index){
        this.$router.push({ name: 'detail', params: { arbeit:record } })
        console.log(record);
    }
  }
};
</script>

<style>
</style>