<template>
  <div class="index">
    <!-- <p>Chat, future me.</p> -->
    <base-field :value.sync="value1" placeholder="说点什么吧, 老兄."/>
    <base-field :value.sync="value2" placeholder="说点什么吧, 老兄."/>
    <base-field :value.sync="value3" placeholder="说点什么吧, 老兄."/>
    <base-field :value.sync="value4" placeholder="说点什么吧, 老兄."/>
  </div>
</template>

<script>
export default {
  name: 'index',
  components: {
    'base-field': () => import('@/components/base/base-field')
  },
  data () {
    return {
      value1: '',
      value2: '',
      value3: '',
      value4: '',
    }
  }
}
</script>

<style lang="stylus" scoped>
</style>
