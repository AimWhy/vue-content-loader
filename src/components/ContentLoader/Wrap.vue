<template>
  <svg :viewBox="`0 0 ${width} ${height}`" :style="styleObj" :preserveAspectRatio="preserveAspectRatio" :class="className">
    <defs>
      <clipPath :id="idClip">
        <slot></slot>
      </clipPath>
      <linearGradient :id="idGradient">
        <stop offset="0%" :stop-color="primaryColor" :stop-opacity="primaryOpacity">
          <animate v-if="animate" attributeName="offset" :values="animationValues[0]" :dur="`${speed}s`" repeatCount="indefinite"/>
        </stop>

        <stop offset="50%" :stop-color="secondaryColor" :stop-opacity="secondaryOpacity">
          <animate v-if="animate" attributeName="offset" :values="animationValues[1]" :dur="`${speed}s`" repeatCount="indefinite"/>
        </stop>

        <stop offset="100%" :stop-color="primaryColor" :stop-opacity="primaryOpacity">
          <animate v-if="animate" attributeName="offset" :values="animationValues[2]" :dur="`${speed}s`" repeatCount="indefinite"/>
        </stop>
      </linearGradient>
    </defs>
    <rect :style="{fill: `url(#${idGradient})`}" :clip-path="`url(#${idClip})`" x="0" y="0" :width="width" :height="height" />
  </svg>
</template>

<script>
let uid = () => Math.random().toString(36).substring(2)
let defautlAnimation = [ '-3; 1', '-2; 2', '-1; 3' ]
let rtlAnimation = [ '1; -3', '2; -2', '3; -1' ]

export default {
  name: 'Wrap',
  props: {
    styleObj: {
      type: Object,
      default: function () { return ({}) },
    },
    uniquekey: {
      type: String,
      default: '',
    },
    className: {
      type: [ String, Object, Array ],
      default: '',
    },
    animate: {
      type: Boolean,
      default: true,
    },
    width: {
      type: Number,
      default: 400,
    },
    height: {
      type: Number,
      default: 130,
    },
    preserveAspectRatio: {
      type: String,
      default: 'xMidYMid meet',
    },
    primaryColor: {
      type: String,
      default: '#f0f0f0',
    },
    primaryOpacity: {
      type: Number,
      default: 1,
    },
    secondaryColor: {
      type: String,
      default: '#e0e0e0',
    },
    secondaryOpacity: {
      type: Number,
      default: 1,
    },
    speed: {
      type: Number,
      default: 2,
    },
    rtl: {
      type: Boolean,
      default: false,
    },
  },
  data () {
    return {
      idClip: this.uniquekey ? `${this.uniquekey}-idClip` : uid(),
      idGradient: this.uniquekey ? `${this.uniquekey}-idGradient` : uid(),
      animationValues: this.rtl ? rtlAnimation : defautlAnimation
    }
  }
}
</script>
