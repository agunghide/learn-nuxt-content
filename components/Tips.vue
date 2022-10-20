<template>
  <div
    class="p-5 text-black rounded-md opacity-80"
    :class="alertType"
  >
    <slot>
      {{ text }}
    </slot>
  </div>
</template>

<script>
export default {
  name: 'AlertComponent',
  props: {
    text: {
      type: String,
      default: null
    },
    type: {
      type: String,
      default: 'primary',
      validator (value) {
        return ['primary', 'success', 'warning', 'danger'].includes(value)
      }
    }
  },
  computed: {
    alertType () {
      let result = ''
      switch (this.type) {
        case 'primary':
          result = 'bg-gray-400'
          break
        case 'success':
          result = 'bg-green-500'
          break
        case 'warning':
          result = 'bg-yellow-500'
          break
        case 'danger':
          result = 'bg-red-500'
          break
        default:
          result = 'bg-gray-400'
          break
      }
      return result
    }
  }
}
</script>
