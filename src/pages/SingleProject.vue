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
                    console.log(this.project);
                });
            }
        },
        mounted() {
            this.getSingleProjectDetailsFromApi();
        }
    }
</script>

<template>
    <div>
        hi i'm single project
    </div>
</template>


<style scoped lang="scss">

</style>