<template>
  <div class="education mt-5">
    <h2><i class="fa fa-graduation-cap" aria-hidden="true"></i> Formations</h2>
    <dl class="text-white">
      <template v-for="(formation, index) in education" >
        <dt :key="`degree-${index}`">{{ formation.degree }}</dt>
        <dd :key="`period-${index}`" class="text-white-50">
          {{ formation.period }} - {{ formation.school }}
        </dd>
      </template>
    </dl>
  </div>
</template>

<script>
export default {
  name: 'Education',
  props: {
    education: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
