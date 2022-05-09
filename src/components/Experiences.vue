<template>
  <div class="experiences mb-5">
    <ul class="timeline">
      <li
          v-for="(experience, index) in experiences"
          :key="`experience-${index}`"
          class="with-page-break">
        <h3 :key="`position-${index}`">{{ experience.position }}</h3>
        <h4 :key="`company-${index}`">{{ experience.company }}
          <span v-if="experience.website">- </span>
          <a v-if="experience.website" :href="experience.website">{{ experience.website }}</a>
          <small class="text-muted float-right">
            <i class="fa fa-calendar"></i> {{ experience.timeperiod }}
          </small>
        </h4>
        <p :key="`description-${index}`">{{ experience.description }}
          <ul v-if="experience.list">
            <li v-for="(item, index) in experience.list" :key="index"
                v-html="item.replace(/\n/g, '<br>')">
              {{ item }}
            </li>
          </ul>
        </p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Experiences',
  props: {
    experiences: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  h3 {
    font-size: 18px;
  }
  h4 {
    font-size: 16px;
    color: #44536F;
  }
  ul.timeline {
    list-style-type: none;
    position: relative;
  }
  ul.timeline:before {
    content: ' ';
    background: #d4d9df;
    display: inline-block;
    position: absolute;
    margin-top: 5px;
    left: 18px;
    width: 2px;
    height: 100%;
    z-index: 400;
  }
  ul.timeline > li {
    margin: 20px 0;
    padding-left: 20px;
  }
  ul.timeline > li:before {
    content: ' ';
    background: white;
    display: inline-block;
    position: absolute;
    border-radius: 50%;
    border: 3px solid #ffc107;
    left: 10px;
    margin-top: 3px;
    width: 20px;
    height: 20px;
    z-index: 400;
  }
</style>
