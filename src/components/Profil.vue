<template>
  <div class="profile mt-1 mb-3">
    <img
      alt="moi"
      src="../assets/me.png"
      style="max-width: 150px;"
      class="rounded bg-transparent mx-auto d-block mb-2 img-thumbnail" />
    <h1 class="text-center name">{{ me.name }}</h1>
    <h2 class="text-center title">{{ me.title }}</h2>
    <p class="ml-4 ">
      <i class="fa fa-envelope mr-2" aria-hidden="true" />&nbsp;
      <a :href="`mailto:${me.contact.email}`" class="">{{ me.contact.email }}</a>
    </p>
    <p class="ml-4">
      <i class="fa fa-phone mr-2" aria-hidden="true" />&nbsp;
      <a :href="`tel:${me.contact.phone}`" class="">{{ me.contact.phone }}</a>
    </p>
    <p class="ml-4">
      <i class="fa fa-map-marker mr-2" aria-hidden="true" /> {{ me.location }}
    </p>
    <p class="ml-4">
      <i class="fa fa-birthday-cake mr-2" aria-hidden="true" />&nbsp;
      &nbsp; {{ new Date().getFullYear() - me.birth }} ans
    </p>
    <div class="row mt-3 --hide-from-pdf d-print-none">
      <div class="col-3 text-center">
        <a :href="me.contact.github" class="">
          <i class="fa fa-github fa-2x" aria-hidden="true" />&nbsp;
        </a>
      </div>
      <div class="col-3 text-center">
        <a :href="me.contact.linkedin" class="">
          <i class="fa fa-linkedin fa-2x" aria-hidden="true" />&nbsp;
        </a>
      </div>
      <div class="col-3 text-center">
        <a :href="me.contact.twitter" class="">
          <i class="fa fa-twitter fa-2x" aria-hidden="true" />&nbsp;
        </a>
      </div>
      <div class="col-3 text-center">
        <a href="CV.pdf">
          <i class="fa fa-file-pdf-o fa-2x" aria-hidden="true" />
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'profil-item',
  props: {
    me: {
      type: Object,
      required: true,
    },
  },
  methods: {
    generatePdf() {
      /* eslint-disable */
      SejdaJsApi.htmlToPdf({
        filename: 'cv-benoit-norrin.pdf',
        /* leave blank for one long page */
        pageSize: 'a4',
        publishableKey: 'api_public_209885597d6049fda058e015f219f8d6',
        htmlCode: document.querySelector('html'),
        /* url: window.location.href */
        always: function(){
          // PDF download should have started
        }
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .profile, .profile a {
    color: white;
  }
  .profile .title {
    color: black;
  }
  .profile li {
    font-size: 16px;
  }

</style>
