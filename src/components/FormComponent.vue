<template>
  <div class="form-container">
    <label for="name">Nombre:</label>
    <input class="form-item" type="text" id="name" placeholder="Introduzca su nombre" v-model="name">
    <label for="age">Edad:</label>
    <input class="form-item" type="text" id="age" placeholder="Introduzca su edad" v-model="age">
    <label for="company">Empresa:</label>
    <input class="form-item" type="text" id="company" placeholder="Introduza su empresa" v-model="company">
  </div>
</template>

<script>
import { reactive, toRefs } from '@vue/reactivity'
import { watch } from '@vue/runtime-core'
export default {
  name: 'FormComponent',
  emits: ['formChanged'],
  setup(props, {emit}) {
    const state = reactive({
      name: '',
      age: '',
      company: ''
    })

    watch(state, (newVal) => {
      emit('formChanged', newVal)
    })

    return {...toRefs(state)}

  }
}
</script>

<style scoped>
.form-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.form-item {
  padding: 5px;
  margin: 5px;
}
</style>