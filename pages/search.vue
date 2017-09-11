<template>
  <div>
    <input type="text" v-model="srch">
    <div>The current query is: {{srch}}</div>
    <div>The srch param in the url query is: {{querySrch}}</div>
  </div>
</template>

<script>
export default {
  data () {
    console.log('search rebuild?')
    return {
      srch: this.$router.currentRoute.query.srch,
      querySrch: this.$router.currentRoute.query.srch
    }
  },
  computed: {
    routeQuery () {
      return this.$router.currentRoute.query.srch
    }
  },
  watch: {
    routeQuery (querySrch) {
      console.log('watch querySrch', querySrch)
    },
    srch (srch) {
      console.log('watch srch', srch)
      this.$router.replace({name: 'search', query: {srch: srch}})
    }
  },
  beforeRouteUpdate (to, from, next) {
    console.log(to, from, next)
    next()
  }
}
</script>