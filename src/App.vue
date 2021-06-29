<template>
  <div id="app">
    <Button
      class="green"
      @setStars="setStars"
    />
    <Modal
      v-if="isStars"
      :countStars="countStars"
      @setStars="setStars"
      @setCountStars="setCountStars"
    />
    <div
      v-else
      class="stars-text"
    >Stars: {{countStars}}</div>
  </div>
</template>

<script>
import Modal from '@/components/Modal'
import Button from '@/components/Button'

export default {
  name: 'App',
  components: {
    Modal,
    Button
  },
  data() {
    return {
      isStars: false,
      countStars: 0,
    }
  },
  methods: {
    setStars() {
      this.isStars = !this.isStars
    },
    setCountStars(num) {
      this.countStars = parseInt(num)
    },
  },
}
</script>

<style scoped>
.stars-text {
  font-family: Arial, Helvetica, sans-serif;
  margin: 20px 0;
}
</style>
