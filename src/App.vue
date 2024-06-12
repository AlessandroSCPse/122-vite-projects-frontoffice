<script>
import ProjectsList from './components/ProjectsList.vue';
import AppHeader from './components/AppHeader.vue';

export default {
  components: {
    ProjectsList,
    AppHeader
  }
}
</script>

<template>
  <AppHeader></AppHeader>
  <router-view></router-view>
</template>

<style lang="scss">
@use './style/generic';
</style>