<template>
    <form id="form" class="create-project-home">
        <div class="card">
            <div class="card-body">
                <div class="form-group">
                    <a role="button">
                        <div class="md-field md-field--modify-label md-theme-default md-has-placeholder">
                            <input @click="showProjectDescription" type="text" id="md-input-mys94sok" placeholder="Project Name" maxlength="100" class="md-input" v-model="projectName" @focusin="addFocusClass" @focusout="removeFocusClass">
                            <span class="md-error"></span>
                            <span class="md-count"> {{countProjectName}} / 100 </span>
                        </div>
                    </a>
                </div>
                <transition name="slide">
                <div id="collapse_desc" class="collapse" :class="{show: isShowProjectDescription}" :key="isShowProjectDescription">
                    <div class="form-group">
                        <div class="md-field md-field--modify-label md-theme-default md-has-placeholder md-has-textarea">
                            <textarea id="md-textarea-b6felq2dr" placeholder="Project Description" maxlength="500" class="md-textarea md-scrollbar" style="resize: none;" v-model="projectDescription" @focusin="addFocusClass" @focusout="removeFocusClass"></textarea>
                            <span class="md-error"></span>
                            <span class="md-count"> {{countProjectDescription}} / 500 </span>
                        </div>
                    </div>
                    <div style="text-align: center;">
                        <button type="button" class="md-button onCancelButtonClick md-theme-default" @click="hideProjectDescription">
                            <div class="md-ripple">
                                <div class="md-button-content"> Cancel </div>
                            </div>
                        </button>
                        <button :disabled="isCreateButtonDisabled" type="button" class="md-button md-raised md-primary md-theme-default" @click="addProject">
                            <div class="md-ripple md-disabled">
                                <div class="md-button-content"> Create </div>
                            </div>
                        </button>
                    </div>
                </div>
                </transition>
            </div>
        </div>
    </form>
</template>

<script>
export default {
  name: 'ProjectHome',
  data () {
    return {
      projectDescription: '',
      projectName: '',
      countProjectName: 0,
      countProjectDescription: 0,
      isShowProjectDescription: false,
      isCreateButtonDisabled: true
    }
  },
  methods: {
    showProjectDescription: function () {
      this.isShowProjectDescription = this.isShowProjectDescription ? this.isShowProjectDescription : !this.isShowProjectDescription
    },
    hideProjectDescription: function () {
      this.isShowProjectDescription = this.isShowProjectDescription ? !this.isShowProjectDescription : this.isShowProjectDescription
    },
    addProject: function () {
      var projects = localStorage.projects ? JSON.parse(localStorage.projects) : []
      var data = {
        name: this.projectName,
        description: this.projectDescription
      }
      projects.push(data)
      window.localStorage.projects = JSON.stringify(projects)
      this.$emit('updateProjects')
      this.projectName = ''
      this.projectDescription = ''
      this.hideProjectDescription()
    },
    addFocusClass: function (event) {
      event.target.parentElement.classList.add('md-focused')
    },
    removeFocusClass: function (event) {
      event.target.parentElement.classList.remove('md-focused')
    },
    clickWindow: function (event) {
      if (!event.target.closest('.create-project-home')) {
        this.hideProjectDescription()
      }
    }
  },
  created: function () {
    window.addEventListener('click', this.clickWindow)
  },
  watch: {
    projectName (newValue, oldValue) {
      if (this.projectName && this.projectDescription) {
        this.isCreateButtonDisabled = false
      } else {
        this.isCreateButtonDisabled = true
      }

      this.countProjectName = newValue.length
      if (this.countProjectName > 100) {
        this.countProjectName = 100
        this.projectName = oldValue
      }
    },
    projectDescription (newValue, oldValue) {
      if (this.projectName && this.projectDescription) {
        this.isCreateButtonDisabled = false
      } else {
        this.isCreateButtonDisabled = true
      }

      this.countProjectDescription = newValue.length
      if (this.countProjectDescription > 500) {
        this.countProjectDescription = 500
        this.projectName = oldValue
      }
    }
  }
}

</script>

<style>
.slide-enter-active {
   -moz-transition-duration: 0.5s;
   -webkit-transition-duration: 0.5s;
   -o-transition-duration: 0.5s;
   transition-duration: 0.5s;
   -moz-transition-timing-function: ease-in;
   -webkit-transition-timing-function: ease-in;
   -o-transition-timing-function: ease-in;
   transition-timing-function: ease-in;
}

.slide-leave-active {
   -moz-transition-duration: 0.5s;
   -webkit-transition-duration: 0.5s;
   -o-transition-duration: 0.5s;
   transition-duration: 0.5s;
   -moz-transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
   -webkit-transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
   -o-transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
   transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
}

.slide-enter-to, .slide-leave {
   max-height: 200px;
   overflow: hidden;
}

.slide-enter, .slide-leave-to {
   overflow: hidden;
   max-height: 0;
}
</style>
