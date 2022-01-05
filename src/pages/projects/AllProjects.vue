<template>
  <div class="columns">
    <div class="column">

      <b-field label="Search Projects">
        <b-input v-model="searchTerm"></b-input>
      </b-field>

      <div class="card" v-for="project in filteredProjects"
      :key="project.id">
        <div class="card-image">
          <figure class="image is-4by3">
            <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
          </figure>
        </div>
        <div class="card-content">
          <div class="media">
            <!-- <div class="media-left">
              <figure class="image is-48x48">
                <img src="https://bulma.io/images/placeholders/96x96.png" alt="Placeholder image">
              </figure>
            </div> -->
            <div class="media-content">
              <p class="title is-4">{{ project.title }}</p>
              <p class="subtitle is-6">
                <b-taglist>
                  <b-tag
                   v-for="tag in project.tags"
                   :key="tag"
                   type="is-primary"
                  >
                    {{tag}}
                  </b-tag>
                </b-taglist>
              </p>
              <router-link v-if="project.demo" :to="{name: project.demo}">Demo</router-link>
              <p v-if="project.links.deployment" >Copy and Paste this Link: <router-link :to="project.links.deployment">{{project.links.deployment}}</router-link> to view deployment</p>

              
            </div>
          </div>
          <div class="content">
            {{ project.description}}
          </div>
        </div>
      </div>
    </div>
      <!-- <input type="text" v-model="searchTerm"/> -->
      
        
  </div>
</template>

<script>
export default {
  name: 'AllProjects',

  data(){
    return{
      projects:[],
      searchTerm: ""
    } 
  },
  computed:{
    filteredProjects: function(){
      return this.projects.filter(project =>{
        return project.title.toLowerCase().includes(this.searchTerm.toLowerCase())

      })
    }
  },

  mounted(){
    this.getAllProjects();
  },

  methods:{

    getAllProjects(){

      fetch('./data/projects.json')
      .then(res => res.json())
      .then(data => {
        console.log(data)
        this.projects = data;
      })

    }

    
  }
}
</script>

<style>

</style>