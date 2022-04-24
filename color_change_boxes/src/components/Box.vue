<template>
  <div
    ref="ref1"
    class="box-container"
    :style="{ 'background-color': backgroundColor }"
    @click="boxClicked">
    <span>{{message}}</span>
  </div>
</template>


<script>
import { ref } from 'vue'

export default{
  props: {
    message: String
  },
  setup(props){
    const divRef = ref(null)

    // Expose to template
    return { props, divRef }
  },
  data(){
    return{
      red: 0,
      green: 0,
      blue: 0
    }
  },
  computed: {
    backgroundColor: function(){
      return `rgb(${this.red}, ${this.green}, ${this.blue})`
    }
  },
  mounted: function() {
    this.changeBoxColor()
  },
  methods: {
    // Detect box is clicked
    boxClicked(){
      this.$emit("boxClicked")
    },

    // Generate the color code 0 - 255 randomly
    generateRandomColorCode(){
      return parseInt(Math.random() * 255)
    },

    // Change the box color randomly
    changeBoxColor(){
      this.red = this.generateRandomColorCode()
      this.green = this.generateRandomColorCode()
      this.blue = this.generateRandomColorCode()
    }
  }
}
</script>

<style scoped>
.box-container{
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1em;
  cursor: pointer;
  text-align: center;
}
span{ 
  font-weight: bold;
  color: white;
}
</style>
