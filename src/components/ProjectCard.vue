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
        <!-- <img src="..." class="card-img-top" alt="..."> -->
        <div class="card-body">
            <h5 class="card-title">{{ projectInfo.name }}</h5>
            <div v-if="projectInfo.type">
                <strong>Type</strong>:
                {{ projectInfo.type.name }}
            </div>
            <p v-if="projectInfo.summary" class="card-text">{{ projectInfo.summary }}</p>
            <!-- <a href="#" class="btn btn-primary">Go somewhere</a> -->
        </div>
    </div>
</template>
