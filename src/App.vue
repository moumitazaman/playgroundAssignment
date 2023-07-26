<script setup>
import { ref,reactive,computed} from 'vue'
const boxstyle=ref("box")
let properties = reactive({
  perspective: 100,
  rotateX: 0,
  rotateY: 0,
  rotateZ:0
})
const box = computed(() => {
  return {
      transform: `
          perspective(${properties.perspective}px)
          rotateX(${properties.rotateX}deg)
          rotateY(${properties.rotateY}deg)
          rotateZ(${properties.rotateZ}deg)
        `
    }
      
      
})


const reset=()=> {
      properties.perspective = 100
      properties.rotateX = 0
      properties.rotateY = 0
      properties.rotateZ = 0
  }

  const changeStyle =(newstyle) =>{
    boxstyle.value= newstyle

  }


</script>

<template>
  
  <h2>Playground</h2>
    <main>
      <section class="settings">
        <div class="settings-container">
          <label>perspective: {{ properties.perspective }}px;</label>
          <input type="range" min="0" max="999" v-model="properties.perspective" />

          <label>rotateX: {{ properties.rotateX }}deg; </label>
          <input type="range" min="-180" max="180" v-model="properties.rotateX" />

          <label>rotateY: {{ properties.rotateY }}deg; </label>
          <input type="range" min="-180" max="180" v-model="properties.rotateY" />

          <label>rotateZ: {{ properties.rotateZ }}deg; </label>
          <input type="range" min="-180" max="180" v-model="properties.rotateZ" />

          <button type="button" @click.prevent="reset">Reset</button>
          <button type="button" @click.prevent="changeStyle('box')">Box</button>
          <button type="button" @click.prevent="changeStyle('triangle-up')">Triangle</button>

          <button type="button" @click.prevent="changeStyle('circle')">Circle</button>

       
        </div>
      </section>
      <section class="output">
        <div class="box-container">
          <div  :class="boxstyle" :style="box"></div>
        </div>
      </section>
    </main>

  
</template>

<style scoped>


</style>
