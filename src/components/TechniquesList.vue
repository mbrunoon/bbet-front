<template>

    <div class="row">

        <div v-if="reloading" class="d-flex">
            <svg xmlns="http://www.w3.org/2000/svg" width="8em" height="8em" fill="currentColor" class="bi bi-arrow-clockwise reloading reloading-bg" viewBox="0 0 16 16">
                <path fill-rule="evenodd" d="M8 3a5 5 0 1 0 4.546 2.914.5.5 0 0 1 .908-.417A6 6 0 1 1 8 2v1z"/>
                <path d="M8 4.466V.534a.25.25 0 0 1 .41-.192l2.36 1.966c.12.1.12.284 0 .384L8.41 4.658A.25.25 0 0 1 8 4.466z"/>
            </svg>            
        </div>

        <div v-else v-for="group in techniques" v-bind:key="group.name" class="col-lg-12 col-xl-6">
            <h2 class="text-center">{{ group.name }}</h2>
            <ul class="list-group mb-4">
                <li v-for="technique in group.techniques" v-bind:key="this.slugfy(technique.name)" class="list-group-item d-flex">
                    <a href="#" class="stretched-link" data-bs-toggle="modal" v-bind:data-bs-target="'#'+this.slugfy(technique.name)">
                        <b>{{ technique.name }}</b> <small>{{ technique.group }}</small>
                    </a>
                    <span class="ms-auto">
                        <svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 576 512"><!--! Font Awesome Pro 6.0.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. --><path d="M279.6 160.4C282.4 160.1 285.2 160 288 160C341 160 384 202.1 384 256C384 309 341 352 288 352C234.1 352 192 309 192 256C192 253.2 192.1 250.4 192.4 247.6C201.7 252.1 212.5 256 224 256C259.3 256 288 227.3 288 192C288 180.5 284.1 169.7 279.6 160.4zM480.6 112.6C527.4 156 558.7 207.1 573.5 243.7C576.8 251.6 576.8 260.4 573.5 268.3C558.7 304 527.4 355.1 480.6 399.4C433.5 443.2 368.8 480 288 480C207.2 480 142.5 443.2 95.42 399.4C48.62 355.1 17.34 304 2.461 268.3C-.8205 260.4-.8205 251.6 2.461 243.7C17.34 207.1 48.62 156 95.42 112.6C142.5 68.84 207.2 32 288 32C368.8 32 433.5 68.84 480.6 112.6V112.6zM288 112C208.5 112 144 176.5 144 256C144 335.5 208.5 400 288 400C367.5 400 432 335.5 432 256C432 176.5 367.5 112 288 112z"/></svg>                        
                    </span>        
                    
                    <TechniqueModal :name="technique.name" :group="technique.group" :url="technique.url" :slug="this.slugfy(technique.name)" />
                </li>
            </ul>
        </div>
    </div>

</template>

<script>

import axios from 'axios'
import TechniqueModal from './TechniqueModal.vue'

export default {
    name: "TechniquesList",
    components: {
        TechniqueModal
    },
    data(){
        return {
            techniques: [],
            reloading: false
        }
    },

    mounted() {
        this.reloading = true;
        axios.get('https://bbet-api.herokuapp.com').then( res => {
            this.techniques = res.data;
            this.reloading = false;
        })
    },
    
    methods: {
        slugfy(stringToSlugfy) {
            return stringToSlugfy.toLowerCase()
                    .replace(/[^a-z0-9 -]/g, '') // remove invalid chars
                    .replace(/\s+/g, '-') // collapse whitespace and replace by -
                    .replace(/-+/g, '-'); // collapse dashes
        }
    }    
}
</script>
