<template>
  
    <div class="container py-4">

        <div class='row mb-4'>
          <div class='d-grid gap-2 d-flex justify-content-end'>
            <button class="btn btn-outline-primary" @click="reloadTechniquesList">
                <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="currentColor" class="bi bi-arrow-clockwise" viewBox="0 0 16 16">
                  <path fill-rule="evenodd" d="M8 3a5 5 0 1 0 4.546 2.914.5.5 0 0 1 .908-.417A6 6 0 1 1 8 2v1z"/>
                  <path d="M8 4.466V.534a.25.25 0 0 1 .41-.192l2.36 1.966c.12.1.12.284 0 .384L8.41 4.658A.25.25 0 0 1 8 4.466z"/>
                </svg>
            </button>
          </div>
        </div>

        <TechniquesList v-bind:key="techiniquesListKey"/>
        
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
      console.log(this.techiniquesListKey)
      this.techiniquesListKey++
    }
  }
}
</script>