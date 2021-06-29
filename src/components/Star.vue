<template>
  <div ref="starId" @click="clickOnStar">
    <img v-if="!checked" src="@/assets/star_w.svg">
    <img v-else src="@/assets/star_b.svg">
  </div>
</template>

<script>
  export default {
    name: 'Star',
    props: {
      checked: {
        type: Boolean,
        default: false
      }
    },
    methods: {
      clickOnStar() {
        this.$emit('setCurrentStar', this.$refs.starId.id)
      }
    },
  }
</script>
