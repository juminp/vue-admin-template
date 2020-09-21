<template>
  <div style="padding:30px;">
    <el-alert :closable="false" title="menu 1-1" type="success">
      <router-view />
    </el-alert>
  </div>
</template>
<script>

export default {
  name: 'Dashboard',
  data() {
    return {}
  },
  created() {
    const id = this.$route.params && this.$route.params.id
    // set tagsview title
    this.setTagsViewTitle(id)

    // set page title
    this.setPageTitle(id)
  },
  methods: {
    setTagsViewTitle(id) {
      const title = '详情'
      const route = Object.assign({}, Object.assign({}, this.$route), { title: `${title}-${id}` })
      this.$store.dispatch('tagsView/updateVisitedView', route)
    },
    setPageTitle(id) {
      const title = '详情'
      document.title = `${title} - ${id}`
    }
  }
}
</script>
