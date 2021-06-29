<template>
    <button class="btn" @click="$emit('setStars')">
      {{titleButton}}
    </button>
</template>

<script>
  export default {
    name: 'Button',
    props: {
      titleButton: {
        type: String,
        default: 'Button'
      },
    },
  }
</script>

<style scoped>
.btn {
  border-radius: 2px;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  cursor: pointer;
  transition-duration: 0.4s;
}
.btn:hover {
  box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);
}
.green {
  background-color: #4caf4fa6;
  border: 2px solid #4CAF50;
  color: white;
}
.green:hover {
  background-color: #4CAF50;
  color: white;
  border: 2px solid #4CAF50;
}
.red {
  background-color: rgba(255, 99, 71, 0.6);
  border: 2px solid tomato;
  color: white;
}
.red:hover {
  background-color: tomato;
  color: white;
  border: 2px solid tomato;
}
</style>