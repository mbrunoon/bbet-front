<template>

    <div class="modal fade" v-bind:id="slug" tabindex="-1" v-bind:aria-labelledby="name" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">{{ name }} <small class="h6">({{ group }})</small></h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <div v-if="url">
                        <iframe width="100%" src="https://www.youtube.com/watch?v=B2EI65ZEqYQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                    </div>
                    <div v-else>
                        <p class="alert alert-info text-center"><b>Video coming soon</b></p>
                    </div>
                </div>
            </div>
        </div>
    </div>

</template>

<script>

    export default {
        name: "TechniqueModal",
        props: {
            name: String,
            url: String,
            group: String,
            slug: String
        },
        data(){
            return{

            }
        }
    }

</script>
