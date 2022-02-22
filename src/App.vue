<template>
  
  <div class="navbar navbar-dark bg-dark mb-4">
    <div class="container-fluid">

      <span class="navbar-brand">BBET</span> 

          <div class='d-flex justify-content-end col-4'>
            <button class="btn btn-primary" @click="reloadTechniquesList" title="Reload techniques">
                <svg xmlns="http://www.w3.org/2000/svg" width="1.8em" height="1.8em" fill="currentColor" class="bi bi-arrow-clockwise" viewBox="0 0 16 16">
                  <path fill-rule="evenodd" d="M8 3a5 5 0 1 0 4.546 2.914.5.5 0 0 1 .908-.417A6 6 0 1 1 8 2v1z"/>
                  <path d="M8 4.466V.534a.25.25 0 0 1 .41-.192l2.36 1.966c.12.1.12.284 0 .384L8.41 4.658A.25.25 0 0 1 8 4.466z"/>
                </svg>
            </button>
          </div>

    </div>
  </div>

  <div class="container py-2">

      <TechniquesList v-bind:key="techiniquesListKey"/>

  </div>

  <div class="container-fluid fixed-bottom py-2 bg-light">
    <div class="row">
      <a href="https://marcosbruno.com" target="blank" class="col-12 text-center small text-dark">Developed by <b>Marcos Bruno</b></a>
    </div>    
  </div>

</template>

<script>

import TechniquesList from './components/TechniquesList.vue'

export default {
  name: 'App',
  title: 'Teste',
  components: {
    TechniquesList
  },
  data: function(){
    return {
      techiniquesListKey: 0
    }
  },
  mounted(){
    document.title = "BBET | Black Belt Exam Training"
  },
  methods: {
    reloadTechniquesList() {
      this.techiniquesListKey++
    }
  }
}
</script>

<style>

    .reloading {
        animation: spin-animation 0.5s infinite;  
    }

    .reloading-bg{
        color:#ccc;  
        position:fixed;  
        top:50%;
        left:50%;
        margin-top:-4em;
        margin-left: -4em;          
    }

    @keyframes spin-animation {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(359deg); }
    }

</style>