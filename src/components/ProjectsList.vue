<script>
import axios from 'axios';
    export default {
        name: 'ProjectsList',
        data() {
            return {
                projects : [],
            };
        },
        methods: {
            getProjects() {
                // Chiamata axios a BackEnd con API
                axios.get('http://127.0.0.1:8000/api/projects')
                .then((response) => {
                    this.projects = response.data.results;
                    // console.log(this.projects);
                })
            }
        },
        mounted() {
            this.getProjects();
        }
    }
</script>

<template>
<div class="container">
    <h1 class="text-center mt-2 mb-4">Projects List</h1>
    <div class="row row-cols-3">
        <!-- Single card -->
        <div class="col my-2" v-for="project in projects">
            <div class="card">
                <!-- <img src="..." class="card-img-top" alt="..."> -->
                <div class="card-body">
                    <h3 class="card-title">{{ project.name }}</h3>
                    <p class="card-text my-2">
                        <strong>Client Name</strong>: <span class="fw-light">{{ project.client_name }}</span>
                    </p>
                    <div v-if="project.type" class="card-text my-2">
                        <strong>Project Type</strong>: <span class="fw-light">{{ project.type.name }}</span>
                    </div>
                    <div v-if="project.technologies.length > 0" class="card-text my-2">
                        <strong>Technologies</strong>: <span v-for="techs in project.technologies" class="fw-light">{{ techs.name }}&nbsp;</span>
                    </div>
                    <p v-if="project.summary" class="card-text my-2">
                        <strong>Project Summary</strong>: <span class="fw-lighter">{{ project.summary }}</span>
                    </p>
                    <!-- <a href="#" class="btn btn-primary">Go somewhere</a> -->
                </div>
            </div>
        </div>
        <!-- /Single card -->
    </div>
</div>
</template>


<style scoped lang="scss">

</style>