<template>
  <ul>
    <learning-resources
      :key="res.id"
      :valor="res"
      :deleteElement="deleteResource"
      v-for="res in resources"
    ></learning-resources>
  </ul>
</template>

<script>
import LearningResources from './LearningResources';
export default {
  components: { LearningResources },
  inject: ['resources', 'deleteResource']
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
