<template>
  <div class="home w-screen h-screen flex items-center justify-center select-none">
    <div class="">
      <div class="flex mb-1 justify-between" v-for="(row, rowIndex) in rows" :key="rowIndex+'row'">
        <div class="h-12 relative mx-2px" :style="getKeycapWidth(keycap)" v-for="(keycap, keycapIndex) in row" :key="keycapIndex+'keycap'">
          <div class="w-full flex justify-center absolute z-20">
            <div class="h-34px mt-1 shadow-sm rounded-sm" :style="getSmallStyle(keycap)"></div>
          </div>
          <div class="absolute inset-0 z-10 rounded bg-black opacity-10"></div>
          <div class="w-12 h-12 absolute z-0 rounded" :style="getKeycapStyle(keycap)"></div>
        </div>
      </div>
      <div class="mt-24 flex justify-between">
        <chrome-picker v-model="colors['extras']" @input="updateExtras"/>
        <chrome-picker v-model="colors['alphas']" @input="updateAlphas"/>
        <chrome-picker v-model="colors['modifiers']" @input="updateModifiers"/>
      </div>
    </div>
  </div>
</template>

<script>
import { Photoshop, Material, Compact, Swatches, Slider, Sketch, Chrome } from 'vue-color'

export default {
  name: 'Home',
  components: {
    'material-picker': Material,
    'compact-picker': Compact,
    'swatches-picker': Swatches,
    'slider-picker': Slider,
    'sketch-picker': Sketch,
    'chrome-picker': Chrome,
    'photoshop-picker': Photoshop,
  },
  data() {
    return {
      colors2: '#194D33A8',
      colors: {
        extras: '#7E789A',
        alphas: '#F8F9FC',
        modifiers: '#373244',
      },
      rows: [
        [
          [1, 'extras'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [2, 'modifiers']
        ],
        [
          [1.5, 'modifiers'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1.5, 'modifiers']
        ],
        [
          [1.75, 'modifiers'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [2.25, 'extras'],
        ],
        [
          [2.25, 'modifiers'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [1, 'alphas'],
          [2.75, 'modifiers'],
        ],
        [
          [1.25, 'modifiers'],
          [1.25, 'modifiers'],
          [1.25, 'modifiers'],
          [6.25, 'alphas'],
          [1.25, 'alphas'],
          [1.25, 'alphas'],
          [1.25, 'modifiers'],
          [1.25, 'modifiers'],
          [1.25, 'modifiers'],
        ],
      ]
    }
  },
  methods: {
    getKeycapColor(keycap) {
      return 'background-color:' + this.colors[keycap[1]]
    },
    getKeycapWidth(keycap) {
      let width = keycap[0] * 48
      return 'width:' + width.toString() + 'px'
    },
    getKeycapStyle(keycap) {
      let width = keycap[0] * 48
      return 'width:' + width.toString() + 'px'  + ';' + 'background-color:' + this.colors[keycap[1]]
    },
    getSmallStyle(keycap) {
      let width = keycap[0] * 48 - 14
      return 'width:' + width.toString() + 'px'  + ';' + 'background-color:' + this.colors[keycap[1]]
    },
    updateExtras(value) {
      this.colors['extras'] = value.hex
    },
    updateAlphas(value) {
      this.colors['alphas'] = value.hex
    },
    updateModifiers(value) {
      this.colors['modifiers'] = value.hex
    }
  }
}
</script>
