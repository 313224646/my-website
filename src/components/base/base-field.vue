<template>
  <div class="van-hairline--top">
    <van-field 
      class="field"
      :class="{'field--active': fieldActive}"
      v-model="inValue"
      ref="field"
      :border="false"
      @input="$emit('update:value', inValue)"
      @focus="setFidleActive('focus')"
      @blur="setFidleActive('blur')"
    />
  </div>
</template>

<script>
import { Field } from 'vant'
export default {
  name: 'field',
  components: {
    [Field.name]: Field
  },
  props: {
    value: String,
    placeholder: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      inValue: this.value,
      fieldActive: !!this.value.length
    }
  },
  methods: {
    setFidleActive (behavior) { // behavior: focus or blur
      if (behavior === 'focus' && !this.fieldActive) {
        this.fieldActive = true
      } else if (behavior === 'blur' && !this.inValue.length) {
        this.fieldActive = false
      } else {
        console.log('Missing parameters')
      }
    }
  },
  mounted () {
    this.$refs.field.$el.setAttribute('data-placeholder', this.placeholder)
  }
}
</script>

<style lang="stylus" scoped>
.field
  overflow inherit
  transition margin-top .4s
  &:before
    transition transform .4s
    content attr(data-placeholder)
    position absolute
    color #bfbec3
.field--active
  margin-top 20px
  &:before
    color #9768ff
    transform translateY(-32px)
</style>
