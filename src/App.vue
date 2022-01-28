<template>
<div class="container">
<div>
  <card-component v-model:age="age" v-model:name="name" v-model:themeMode="themeMode" v-model:company="company"/>
</div>
<div>
  <form-component @formChanged="formComponentChanged"/>
  <radio-component @optionChanged="radioOptionChanged" :default="themeMode" :options="[{label: 'Xbox', value: 'xbox'}, {label: 'PLaystation', value: 'ps'}]"/>
  </div>
</div>
</template>

<script>
import { reactive, toRefs } from '@vue/reactivity'
import RadioComponent from './components/RadioComponent.vue'
import FormComponent from './components/FormComponent.vue'
import CardComponent from './components/CardComponent.vue'

export default {
  name: 'App',
  components: {
    RadioComponent,
    FormComponent,
    CardComponent
  },
  setup() {
    const state = reactive({
      themeMode: 'xbox',
      name: '',
      age: '',
      company: ''
    })
    function radioOptionChanged(themeMode) {
      console.log(themeMode)
      state.themeMode = themeMode;
    }

    function formComponentChanged({name, age, company}) {
      state.name = name;
      state.age = age;
      state.company = company;
    }
    return {...toRefs(state), radioOptionChanged, formComponentChanged}
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}

.container {
  display:flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  max-width: 1200px;
}
</style>
