<script setup>
import Box from './components/Box.vue'
</script>

<template>
  <main>
    <!-- Upper part -->
    <div class="flex flex-row">
      <Box 
        class="col"
        message="1"
        ref="box1"
        @box-clicked="detectBoxClicked" />
      <div
        class="col flex flex-col">
        <Box
          ref="box2"
          message="2"
          @box-clicked="detectBoxClicked" />
        <div
          class="col flex flex-fixed-row flex-mobile-first">
          <Box
            class="col"
            message="3"
            ref="box3"
            @box-clicked="detectBoxClicked" />
          <Box 
            class="col"
            message="4"
            ref="box4"
            @box-clicked="detectBoxClicked" />
        </div>
      </div>
    </div>


    <!-- Lower part -->
    <div class="mt-1 flex flex-fixed-row flex-wrap">
      <div class="col">
        <div class="flex flex-fixed-col">
          <Box message="5" ref="box5" @box-clicked="detectBoxClicked" />
          <Box message="6" ref="box6" @box-clicked="detectBoxClicked" />
        </div>
      </div>

      <Box 
        class="col flex-mobile-first flex-mobile-width-100"
        message="7"
        ref="box7"
        @box-clicked="detectBoxClicked" />
        
      <div class="col">
        <div class="flex flex-fixed-col">
          <Box message="8" ref="box8" @box-clicked="detectBoxClicked" />
          <Box message="9" ref="box9" @box-clicked="detectBoxClicked" />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default{
  data(){
    return {
      boxes: ["box1", "box2", "box3", "box4", "box5", "box6", "box7", "box8", "box9"]
    }
  },
  components: {
    Box
  },
  methods: {
    detectBoxClicked(){
      // Change all boxes' color
      this.boxes.forEach(box=>this.$refs[box].changeBoxColor())
    }
  }
}
</script>

<style>
#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-family: -apple-system, 'Segoe UI', sans-serif;
  font-weight: normal;
}

.mt-1 { margin-top: 1rem; }

.flex { 
  display: flex;
  gap: 1rem;
}
.flex-wrap { flex-wrap: wrap; }
.flex-nowrap { flex-wrap: nowrap; }
.flex-row{ flex-direction: row; }
.flex-col{ flex-direction: column;}
.flex-fixed-row { flex-direction: row !important; }
.flex-fixed-col { flex-direction: column !important; }
.col { flex: 1 }

@media (max-width: 600px){
  .flex-row { flex-direction: column; }
  .flex-mobile-width-100 { flex-basis: 100%; }
  .flex-mobile-first { order: -1; }
}
</style>
