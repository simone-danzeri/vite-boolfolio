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
        <div class="col">
            <div class="card">
                <!-- <img src="..." class="card-img-top" alt="..."> -->
                <div class="card-body">
                    <h5 class="card-title">Card title</h5>
                    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                    <!-- <a href="#" class="btn btn-primary">Go somewhere</a> -->
                </div>
            </div>
        </div>
    </div>
</div>
</template>


<style scoped lang="scss">

</style>