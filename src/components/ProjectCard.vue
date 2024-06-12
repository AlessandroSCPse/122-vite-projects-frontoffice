<script>
export default {
    name: 'ProjectCard',
    props: {
        projectInfo: Object
    }
}
</script>

<template>
    <div class="card my-3">
        <div class="card-body">
            <h5 class="card-title">{{ projectInfo.name }}</h5>
            <div v-if="projectInfo.type">
                <strong>Type</strong>:
                {{ projectInfo.type.name }}
            </div>
            <p v-if="projectInfo.summary" class="card-text">{{ projectInfo.summary }}</p>
            <router-link :to="{name: 'single-project', params: {'slug': projectInfo.slug}}" class="btn btn-primary">Read more...</router-link>
        </div>
    </div>
</template>
