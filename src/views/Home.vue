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
        >
            <template slot="actions" slot-scope="row">
                <!-- We use @click.stop here to prevent a 'row-clicked' event from also happening -->
                <b-button size="sm" @click.stop="info(row.item, row.index, $event.target)" class="mr-1">
                    Info modal
                </b-button>
                <b-button size="sm" @click.stop="row.toggleDetails">
                    {{ row.detailsShowing ? 'Hide' : 'Show' }} Details
                </b-button>
            </template>
        </b-table>
        <b-modal id="modalInfo" size="lg" @hide="resetModal" :title="modalInfo.jobName" ok-only>
            <pre>{{ modalInfo.content }}</pre>
        </b-modal>
    </div>
</template>

<script>
import jobs from "@/my_file.json";
export default {
  data() {
    return {
      modalInfo: { jobName: "", content: "" },
      jobs: jobs.jobs,
      fields: [
        "jobName",
        "jobPublicationDate",
        "jobEmployer",
        "jobLocation",
        "jobStartDate",
        "actions"
      ],
      filter: null
    };
  },
  methods: {
    info(item, index, button) {
      this.modalInfo.jobName = `Row index: ${index}`;
      this.modalInfo.content = JSON.stringify(item, null, 2);
      this.$root.$emit("bv::show::modal", "modalInfo", button);
    },
    resetModal() {
      this.modalInfo.jobName = "";
      this.modalInfo.content = "";
    },
    onFiltered(filteredItems) {
      // Trigger pagination to update the number of buttons/pages due to filtering
      this.totalRows = filteredItems.length;
      this.currentPage = 1;
    }
  }
};
</script>

<style>
</style>