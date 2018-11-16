<template>
 <Wrap v-bind="$attrs" :width="width" :height="height">
   <slot>
     <rect x="0" y="0" rx="5" ry="5" :width="width" :height="height" />
   </slot>
 </Wrap>
</template>

<script>
import Wrap from './Wrap.vue'
export default {
  name: 'ContentLoader',
  inheritAttrs: false,
  components: {
    Wrap
  },
  props: {
    width: {
      type: Number,
      default: 400,
    },
    height: {
      type: Number,
      default: 130,
    },
  },
}
</script>
