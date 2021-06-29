<template>
  <div>
    <div
      id="myModal"
      class="modal"
      @click="closeStars"
    >
      <div class="modal-content">
        <span
          class="close"
          @click="$emit('setStars')"
        >&times;</span>
        <div class="stars-list">
          <Star
            v-for="n in calcStar" :key="n.id"
            :id="`${n.id}`"
            :checked="n.checked"
            @setCurrentStar="setCurrentStar"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Star from '@/components/Star'

  export default {
    name: 'Modal',
    components: {
      Star,
    },
    props: {
      countStars: {
        type: Number,
        default: 0
      },
    },
    data() {
      return {
        currentStar: null,
        stars: [
          {
            id: 1,
            checked: false
          },
          {
            id: 2,
            checked: false
          },
          {
            id: 3,
            checked: false
          },
          {
            id: 4,
            checked: false
          },
          {
            id: 5,
            checked: false
          },
        ],
      }
    },
    mounted () {
      if (this.countStars > 0) {
        this.currentStar = this.countStars
      }
    },
    computed: {
      calcStar() {
        if (this.currentStar > 0) {
          this.stars.forEach(e => {
            e.checked = false
            if (this.currentStar >= e.id) {
              e.checked = true
            }
          });
        }
        return this.stars
      },
    },
    methods: {
      closeStars(e) {
        if (e.target.className === 'modal') {
          this.$emit('setStars')
        }
      },
      setCurrentStar(num) {
        this.currentStar = num
        this.$emit('setCountStars', this.currentStar)
      }
    },
  }
</script>

<style scoped>
.modal {
  font-family: Arial, Helvetica, sans-serif;
  position: fixed;
  z-index: 1;
  padding-top: 100px;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0,0,0);
  background-color: rgba(0,0,0,0.4);
}
.modal-content {
  background-color: #fefefe;
  margin: auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}
.close {
  color: #aaaaaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
}
.stars-list {
  display: flex;
}
</style>