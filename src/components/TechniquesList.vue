<template>

    <div class="row">
        <div v-for="group in techniques" v-bind:key="group.name" class="col-lg-12 col-xl-6">
            <h2 class="text-center">{{ group.name }}</h2>
            <ul class="list-group mb-4">
                <li v-for="technique in group.techniques" v-bind:key="technique.name" class="list-group-item">
                    <b>{{ technique.name }}</b> <small>{{ technique.group }}</small> 
                </li>
            </ul>
        </div>
    </div>

</template>

<script>
import axios from 'axios'

export default {
    name: "TechniquesList",

    data(){
        return {
            techniques: []
        }
    },

    mounted() {
        axios.get('https://bbet-api.herokuapp.com').then( res => {
            this.techniques = res.data;
        } )
    }
}
</script>