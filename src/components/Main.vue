<template>
    <main class="pt-4 page-content-container">
        <div class="prj-home-container d-flex flex-column">
            <ProjectHome @updateProjects="updateProjects"></ProjectHome>
            <ProjectList @updateProjects="updateProjects" :projects="projects"></ProjectList>
        </div>
    </main>
</template>

<script>
import ProjectHome from '@/components/ProjectHome'
import ProjectList from '@/components/ProjectList'

export default {
  data () {
    return {
      projects: window.localStorage.projects ? JSON.parse(window.localStorage.projects) : []
    }
  },
  name: 'Main',
  components: {
    ProjectHome, ProjectList
  },
  methods: {
    updateProjects: function () {
      var projects = JSON.parse(window.localStorage.projects)
      this.projects = projects
    }
  }
}
</script>

<style>

</style>
