<template>
  <b-container>
    <b-row>
      <b-col lg="4" offset-lg="4">
        <b-input-group size="sm" class="mb-2">
          <b-input-group-prepend>
            <b-input-group-text class="bg-light">
              <b-icon icon="search" variant="secondary"></b-icon>
            </b-input-group-text>
          </b-input-group-prepend>

          <b-form-input v-model="searchQuery" placeholder="Filter by author..."/>
        </b-input-group>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: "SearchForm",
  data() {
    return {
      searchQuery: ''
    }
  },
  watch: {
    searchQuery(val) {
      this.$emit('update-search-query', val)
    }
  }
}
</script>

<style scoped>

</style>