<template>
<div v-for="option in options" v-bind:key="option.value">
  <input type="radio" id="option.value" v-bind:value="option.value" v-model="optionSelected" v-on:change="$emit('optionChanged', option.value)">
<label for="option.value">{{option.label}}</label>
</div>
</template>
<script>
import { toRef } from '@vue/reactivity'
export default {
  name: 'RadioComponent',
  props: {
    options: Array,
    default: String
  },
  emits: ['optionChanged'],
  setup(props) {
    const optionSelected = toRef(props, 'default')
    return {optionSelected}
  }
}
</script>

<style>

</style>