<template>
    <div class="md-dialog" md-active="true">
        <div class="md-dialog-container md-theme-default" tabindex="-1">
            <span class="md-dialog-title md-title">Confirm</span>
            <div class="md-dialog-content md-theme-default">Project
                <b>{{project.name}}</b> {{getContentModal(typeModal)}}
            </div>
            <div class="md-dialog-actions">
                <button @click="hideModal" type="button" class="md-button md-theme-default">
                    <div class="md-ripple">
                        <div class="md-button-content">Cancel</div>
                    </div>
                </button>
                <button @click="confirmAction(project, index, typeModal)" type="button" class="md-button md-primary md-theme-default">
                    <div class="md-ripple">
                        <div class="md-button-content">OK</div>
                    </div>
                </button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Modal',
  props: ['project', 'index', 'typeModal'],
  methods: {
    confirmAction: function (project, index, type) {
      var projects = localStorage.projects ? JSON.parse(localStorage.projects) : []
      if (type === 'delete') {
        projects.splice(index, 1)
        window.localStorage.projects = JSON.stringify(projects)
        this.$emit('updateProjects')
        this.$emit('hideModal')
      }
      if (type === 'clone') {
        var data = {
          name: project.name,
          description: project.description
        }
        projects.push(data)
        window.localStorage.projects = JSON.stringify(projects)
        this.$emit('updateProjects')
        this.$emit('hideModal')
      }
    },
    hideModal: function () {
      this.$emit('hideModal')
    },
    getContentModal: function (type) {
      if (type === 'delete') {
        return 'is going to be removed. Are you sure?'
      }
      if (type === 'clone') {
        return 'is going to be copied. Do you want to continue?'
      }
    }
  }
}
</script>

<style>
.md-dialog {
    background: rgba(0, 0, 0, 0.5);
}
</style>
