<template>
  <the-header :title="'Remember me'"></the-header>>
  <the-resources></the-resources>
</template>

<script>
//import StoredResources from '../Otracarpeta/styling components/prj-cmp-03-styling-and-more-components/src/components/learning-resources/StoredResources.vue';
//import storedResources from './components/learning-resources/StoredResources';
import TheResources from './components/learning-resources/TheResources';
import TheHeader from './components/Layout/TheHeader.vue';
export default {
  components: { TheResources, TheHeader }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
