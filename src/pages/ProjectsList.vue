<script>
import axios from 'axios';
import { store } from '../store.js';
import ProjectCard from '../components/ProjectCard.vue';

export default {
    name: 'ProjectsList',
    data() {
        return {
            store,
            projects: [],
            currentPage: 1,
            nextPageUrl: null,
            prevPageUrl: null
        };
    },
    components: {
        ProjectCard
    },
    methods: {
        getProjectsFromApi(dataPage) {
            axios.get(`${this.store.backendUrl}/api/projects`, {
                params: {
                    page: dataPage
                }
            })
            .then((response) => {
                this.projects = response.data.results.data;
                this.currentPage = response.data.results.current_page;
                this.nextPageUrl = response.data.results.next_page_url;
                this.prevPageUrl = response.data.results.prev_page_url;
            });
        }
    },
    mounted() {
        this.getProjectsFromApi(this.currentPage);
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
        
        <nav aria-label="Page navigation example">
            <ul class="pagination">
                <li v-if="prevPageUrl" class="page-item">
                    <a class="page-link" @click="getProjectsFromApi(currentPage - 1)">Previous</a>
                </li>

                <li v-if="nextPageUrl" class="page-item">
                    <a class="page-link" @click="getProjectsFromApi(currentPage + 1)">Next</a>
                </li>
            </ul>
        </nav>
    </div>
</template>