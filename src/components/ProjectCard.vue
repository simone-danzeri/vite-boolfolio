<script>
    export default {
        name: 'ProjectCard',
        props: {
            project: Object
        },
        data() {

        },
        methods: {
            truncateSummary(text) {
                if(text.length > 75) {
                    return text.substr(0, 74) + '...';
                }
                return text;
            }
        }
    }
</script>

<template>
        <!-- Single card -->
        <div class="col my-2">
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
                        <strong>Project Summary</strong>: <span class="fw-lighter">{{ truncateSummary(project.summary) }}</span>
                    </p>
                    <!-- <a href="#" class="btn btn-primary">Go somewhere</a> -->
                </div>
            </div>
        </div>
        <!-- /Single card -->
</template>


<style scoped lang="scss">

</style>