<template>
  <div class="hobbies">
    <h2><i class="fa fa-heart"></i> Centres d'intérêts</h2>
    <ul class="text-white-50 list-unstyled">
      <li v-for="(hobby, index) in hobbies" :key="index">{{ hobby }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Hobbies',
  props: {
    hobbies: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
