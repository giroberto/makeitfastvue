<template>
    <div id="detail">
        <div id="property" v-for="(property,index) in arbeitdata" :key="property.jobId">
            <div v-if="checktype(property,'string')">
                <b>{{ index }}</b> - <span v-html="property"></span>
            </div>
            <div v-if="checktype(property,'object')">
                <div id="inner_property" v-for="(innerproperty, innerindex) in property" :key="innerproperty">
                        <b>{{ innerindex }}</b> - <span v-html="innerproperty"></span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
        arbeitdata : this.$route.params.arbeit,
        checktype: function(obj, type) {
            return typeof obj === type
        }
    };
  },
  methods: {
  }
};
</script>