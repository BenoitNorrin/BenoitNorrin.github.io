<template>
  <div>
    <div class="container">
      <div ref="content p-0">
        <div class="row">
          <div class="col-md-4 sidebar">
            <Profil :me="me" />
            <Skills :skills="me.skills" />
            <Education :education="me.education" />
          </div>
          <div class="col-md-8 main">
            <div class="presentation mt-4 mb-5">
              <i class="fa fa-quote-left fa-3x fa-pull-left" /> {{ me.presentation }}
            </div>
            <Experiences :experiences="me.experiences" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import me from '../data.json';
import Experiences from './components/Experiences.vue';
import Profil from './components/Profil.vue';
import Skills from './components/Skills.vue';
import Education from './components/Education.vue';

export default {
  name: 'app',
  components: {
    Education,
    Experiences,
    Profil,
    Skills,
  },
  data() {
    return {
      me,
    };
  },
};
</script>

<style lang="scss">
  $font-size-base: 0.9rem;
  $font-size-sm: 0.9rem;
  $warning: #ff8155;
  @import '~bootstrap';
  @import '../node_modules/font-awesome/css/font-awesome.min.css';

  body {
    font-family: 'Inter', sans-serif;
  }
  .main {
    /* border-right: 2px solid #dc3545; */
  }
  .sidebar {
    background-color: #595959;
  }
  .name {
    font-size: 30px;
  }
  h2 {
    font-size:18px;
    text-transform: uppercase;
    vertical-align: middle;
    background-color: white;
    margin-left: -13px;
    margin-right: -13px;
    padding-left: 13px;
    padding-top: 10px;
    padding-bottom: 10px;
  }
  .title {
    font-size: 20px;
    padding-left: 0px;
  }
  .fa-2x {
    vertical-align: middle;
  }
  .presentation {
    padding: 15px;
    border: 1px solid #ff8155;
    border-radius: 5px;
  }
  .with-page-break {
    page-break-before: always;
    page-break-after: always;
  }
</style>
