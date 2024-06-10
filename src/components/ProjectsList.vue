<script>
import axios from 'axios';
import ProjectCard from './ProjectCard.vue';
    export default {
        name: 'ProjectsList',
        components: {
            ProjectCard,
        },
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
        <ProjectCard v-for="project in projects" :project="project"></ProjectCard>
    </div>
</div>
</template>


<style scoped lang="scss">

</style>