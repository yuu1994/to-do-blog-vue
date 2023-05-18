<template>
  <div class="home">
    <AllProjects></AllProjects>
  </div>
</template>

<script>

import AllProjects from '../components/AllProjects'
export default {
  components: { AllProjects },
  name: 'HomeView',
  
}
</script>

<style>
.home {
  max-width: 1000px;
  margin: 0 auto;
  padding: 10px 0;
}
</style>