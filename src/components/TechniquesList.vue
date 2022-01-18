<template>
    <div class="row">
        <ul v-for="group in techniques" v-bind:key="group.name" class="col-6 list-group">
            <li class="list-group-item text-center"><h1>{{ group.name }}</h1></li>  
            <li v-for="technique in group.techniques" v-bind:key="technique.name" class="list-group-item">
                <b>{{ technique.name }}</b> <small>{{ technique.group }}</small> 
            </li>
        </ul>
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