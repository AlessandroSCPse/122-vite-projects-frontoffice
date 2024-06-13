<script>
import axios from 'axios';
import { store } from '../store.js';
import Loader from '../components/Loader.vue';

export default {
    name: 'SingleProject',
    components: {
        Loader
    },
    data() {
        return {
            store,
            project: null,
            isLoading: false
        };
    },
    methods: {
        getProjectDetails() {
            this.isLoading = true;

            axios.get(`${this.store.backendUrl}/api/projects/${this.$route.params.slug}`)
            .then((response) => {
                if(response.data.success) {
                    this.project = response.data.project;
                } else {
                    this.$router.push({name: 'not-found'});
                }

                this.isLoading = false;
            });
        }
    },
    mounted() {
        this.getProjectDetails();
    }
}
</script>

<template>
    <div class="container">
        <div v-if="project && !isLoading">
            <h1>{{ project.name }}</h1>
            <div v-if="project.client_name"><strong>Client name</strong>: {{ project.client_name }}</div>
            <div v-if="project.type">
                <strong>Type</strong>: {{ project.type.name }}
            </div>

            <div v-if="project.technologies.length > 0">
                <strong>Technologies</strong>
                <div>
                    <div v-for="technology in project.technologies" class="badge rounded-pill text-bg-success">{{ technology.name }}</div>
                </div>
            </div>

            <div v-if="project.cover_image">
                <img :src="`${this.store.backendUrl}/storage/${project.cover_image}`" :alt="project.name">
            </div>

            <p class="mt-5" v-if="project.summary">{{ project.summary }}</p>
        </div>
        <div v-else>
            <Loader></Loader>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.badge {
   margin-right: 5px;
}
</style>