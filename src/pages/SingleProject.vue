<script>
export default {
    name: 'SingleProject'
}
</script>

<template>
    <div class="container">
        <h1>Project name</h1>

        <div>test: {{ $route.params.slug }}</div>
    </div>
</template>
