<template>
  <div class="skills">
    <h2 class="text-black"><i class="fa fa-briefcase" aria-hidden="true" /> Compétences</h2>
    <template v-for="(group, index) in skills">
      <h3 :key="`name-${index}`" class="text-white">{{ group.name }}</h3>
      <ul :key="`ul-${index}`" class="list-unstyled text-white-50">
        <li
          v-for="(scope, index) in group.scopes"
          :key="`li-${index}`"
          class="list-unstyled row mb-1">
          <div class="col-8">
            {{ scope.name }}
          </div>
          <div class="col-4">
            <div class="progress mt-2" style="height: 4px;">
              <div
                class="progress-bar bg-warning"
                :style="`width: ${scope.level}%`"
                :aria-valuenow="scope.level"
                aria-valuemin="0"
                aria-valuemax="100" />
            </div>
          </div>
        </li>
      </ul>
    </template>
    <div class="with-page-break" />
  </div>
</template>

<script>
export default {
  name: 'skills-item',
  props: {
    skills: {
      type: Array,
      required: true,
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  font-size: 15px;
}
</style>
