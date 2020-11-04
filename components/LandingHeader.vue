<template>
  <div>
    <!-- As a heading -->
    <b-navbar toggleable :type="isScroll ? 'dark' : 'light'" :variant="isScroll ? 'dark' : 'light'" fixed="top">
      <b-navbar-brand tag="h1" class="mb-0">{{ Title }}</b-navbar-brand>
      <b-navbar-nav class="ml-auto">
        <b-button size="md" class="my-2 my-sm-0" :variant="isScroll ? 'outline-success' : 'success'" :href="Link" target="_blank">สมัครสมาชิก</b-button>
      </b-navbar-nav>
    </b-navbar>
  </div>
</template>
<script>
export default {
    props: {
      title: String,
      link: String,
    },
    computed: {
      Title () {
        return !this.title ? 'Landing menu' : this.title;
      },
      Link () {
        return !this.link ? 'https://www.google.co.th/' : this.link;
      }
    },
    data () {
      return {
        isScroll: false
      }
    },
    created () {
      window.addEventListener('scroll', this.handleScroll);
    },
    destroyed () {
      window.addEventListener('scroll', this.handleScroll);
    },
    methods: {
      handleScroll (event) {
        if (document.documentElement.scrollTop <= 1) {
          this.isScroll = false;
        } else {
          this.isScroll = true;
        }
        // console.log('--> scroll:', event, document.documentElement.scrollTop);
      }
    }
}
</script>