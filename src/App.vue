<template>
  <div>
    <div class="container">
      <div ref="content p-0">
        <div class="row">
          <div class="col-md-3 sidebar">
            <Profil :me="me"/>
            <Skills :skills="me.skills" />
            <Education :education="me.education" />
            <Hobbies :hobbies="me.hobbies" />
          </div>
          <div class="col-md-9 main">
            <div class="presentation mt-4 mb-5">
              <i class="fa fa-quote-left fa-3x fa-pull-left"></i> {{ me.presentation }}
            </div>
            <Experiences :experiences="me.experiences" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import html2pdf from 'html2pdf.js';
import me from '../data.json';
import Experiences from './components/Experiences.vue';
import Profil from './components/Profil.vue';
import Skills from './components/Skills.vue';
import Education from './components/Education.vue';
import Hobbies from './components/Hobbies.vue';


export default {
  name: 'app',
  components: {
    Hobbies,
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
  methods: {
    generatePdf() {
      /*
      const element = this.$refs.content;
      const opt = {
        margin: 2,
        filename: 'CV-Benoit-Norrin.pdf',
        image: {
          type: 'jpeg',
          quality: 0.98,
        },
        html2canvas: {
          dpi: 192,
          scale: 6,
          letterRendering: true,
        },
        jsPDF: {
          unit: 'mm',
          format: 'a4',
          orientation: 'portrait',
        },
      };
      html2pdf()
        .set(opt)
        .from(element)
        .save();
       */
      /* eslint-disable */
      SejdaJsApi.htmlToPdf({
        filename: 'out.pdf',
        /* leave blank for one long page */
        pageSize: 'a4',
        publishableKey: 'api_public_209885597d6049fda058e015f219f8d6',
        htmlCode: this.$refs.content,
        error: function(err) {
          console.error(err);
          alert('An error occurred');
        }
        /* eslint-enable */
      });
    },
  },
};
</script>

<style lang="scss">
  $font-size-base: 0.9rem;
  $font-size-sm: 0.9rem;
  @import '~bootstrap';
  @import '../node_modules/font-awesome/css/font-awesome.min.css';

  body {
    font-family: 'Roboto', sans-serif;
  }
  .main {
    /* border-right: 2px solid #dc3545; */
  }
  .sidebar {
    background-color: #44536F;
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
    border: 1px solid #ffc107;
    border-radius: 5px;
  }
</style>
