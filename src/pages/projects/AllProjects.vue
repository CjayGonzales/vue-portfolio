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
          <img class="fit_cover" v-if="project.images" :src="require(`@/assets/${project.images}`)" alt="Placeholder image">
        </figure>
      </div>
        <div class="card-content " >
          <div class="media ">
            <!-- <div class="media-left">
              <figure class="image is-48x48">
                <img src="https://bulma.io/images/placeholders/96x96.png" alt="Placeholder image">
              </figure>
            </div> -->
            <div class="media-content ">
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
              <a v-if="project.links.deployment" :href="project.links.deployment" target="_blank">View Website</a>
              <br>
              <a v-if="project.links.github" :href="project.links.github" target="_blank">View Github</a>
              
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

.fit_cover{
  object-fit: cover;
  
}

.dark{
  background-color: black;
}

</style>