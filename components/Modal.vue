<template lang="pug">
div
  .modal(v-bind:class='{open: isOpen}')
    p(v-if="mapConfig") {{mapConfig.map_description}}
    p
      | このサイトのソースコードはオープンに公開しております。開発にご協力いただける方は、
      a(href="https://github.com/codeforjapan/mapprint") Code for Japan の Github リポジトリ
      | から、開発にご参加ください。JavaScript や Leaflet などの経験がある方、大歓迎です。
    div
      span.modal-close(@click='handleClick')
        | × close
  .modal-background(@click='handleClick' :class='{open: isOpen}')
</template>

<script lang="js">
export default {
  props: {
    isOpen: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      mapConfig: this.$nuxt.$route.params.map ? require('~/assets/config/' + (this.$nuxt.$route.params.map)) : ''
    }
  },
  methods: {
    handleClick () {
      this.$emit('update:isOpen', false)
      this.$emit('closeModal')
    }
  }
}
</script>
