<template>
  <select v-bind:value="value" class="select2-enable">
    <option v-for="option in options" v-bind:value="option.value">{{ option.name }}</option>
  </select>
</template>

<script>
  import $ from 'jquery'
  import 'select2'
  import 'select2/dist/css/select2.css'

  export default {
    name: 'select2',
    props: ['value', 'options'],
    mounted () {
      $(this.$el).ready(() => {
        $('.select2-enable').select2({})
        $('.select2-enable').on('change', (e) => {
          this.$emit('input', e.target.value)
        })
      })
    }
  }
</script>
