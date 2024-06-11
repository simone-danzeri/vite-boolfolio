<script>
import axios from 'axios';
    export default {
        name: 'SingleProject',
        data() {
            return {
                project: null
            };
        },
        methods: {
            getSingleProjectDetailsFromApi() {
                axios.get(`http://127.0.0.1:8000/api/projects/${this.$route.params.slug}`)
                .then((response) => {
                    // console.log(response.data.project);
                    this.project = response.data.project;
                });
            }
        },
        mounted() {
            this.getSingleProjectDetailsFromApi();
        }
    }
</script>

<template>
    <div class="container">
        <div v-if="project">
            <h3 class="text-center my-3">{{ project.name }}</h3>
            <div>
                <div class="my-2">
                    <img :src="`http://127.0.0.1:8000/storage/${project.cover_image}`" alt="">
                </div>
                <div class="my-2">
                    <strong>Made for</strong>: 
                    <span v-if="project.client_name" class="fw-light">{{ project.client_name }}</span>
                    <span v-else class="fw-lighter">No client</span>
                </div>
                <div class="my-2">
                    <strong>Project Type</strong>: 
                    <span v-if="project.type" class="fw-lighter">{{ project.type.name }}</span>
                    <span v-else class="fw-lighter">No type selected</span>
                </div>
                <div class="my-2">
                    <strong>Technologies</strong>: 
                    <span v-if="project.technologies.length > 0" v-for="techs in project.technologies" class="fw-lighter">{{ techs.name }}&nbsp;</span>
                    <span v-else class="fw-lighter">No technology selected</span>
                </div>
                <p class=" my-2">
                    <strong>Project Summary</strong>: 
                    <span v-if="project.summary" class="fw-light">{{ project.summary }}</span>
                    <span v-else class="fw-light">No summary</span>
                </p>
            </div>
        </div>
    </div>
</template>


<style scoped lang="scss">
img{
    max-width: 200px;
}
</style>