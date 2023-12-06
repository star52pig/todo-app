<template>
  <el-container>
    <el-header>
      <breadcrumbs />
    </el-header>
    <el-main>
      <router-view />
    </el-main>
  </el-container>
</template>


<script>
import Breadcrumbs from './components/Breadcrumbs.vue';

export default {
  name: 'App',
  components: {
    Breadcrumbs,
  },
};
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
}

.header {
}

.content {
  flex: 1;
  overflow-y: auto;
}

@media (max-width: 600px) {
  #app {
    flex-direction: column;
  }
}
</style>