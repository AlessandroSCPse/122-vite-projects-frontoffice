<script>
import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue';

export default {
    name: 'ProjectsList',
    data() {
        return {
            projects: []
        };
    },
    components: {
        ProjectCard
    },
    methods: {
        getProjectsFromApi() {
            axios.get('http://127.0.0.1:8000/api/projects')
            .then((response) => {
                this.projects = response.data.results;
            });
        }
    },
    mounted() {
        this.getProjectsFromApi();
    }
}
</script>

<template>
    <div class="container">
        <h1>All projects</h1>

        <div class="row row-cols-3">
            <div class="col" v-for="project in projects" :key="project.id">
                <ProjectCard :projectInfo="project"></ProjectCard>
            </div>
        </div>
    </div>
</template>