<template>
    <div class="list-prj-grid">
        <div class="list-prj-grid">
            <strong class="sub-title">All Projects</strong>
            <hr class="mt-1">
            <div class="row justify-content-left">
                <Project v-for="(project, index) in projects" :key="index" :project="project" :index="index" @updateProjects="updateProjects"></Project>
            </div>
        </div>
    </div>
</template>

<script>
import Project from '@/components/Project'

export default {
  name: 'ProjectList',
  props: ['projects'],
  components: {
    Project
  },
  methods: {
    updateProjects: function () {
      this.$emit('updateProjects')
    }
  }
}
</script>

<style>
.my-column {
  min-width: 225px;
}
</style>
