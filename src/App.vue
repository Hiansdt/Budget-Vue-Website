<template>
  <div>
    <Header :totalSobra="state.total" />
  </div>
</template>

<script>
import Header from './components/header.vue'
import {reactive, computed} from 'vue'

export default {
  name: 'App',
  components: {
    Header,
  },
  setup() {

    const state = reactive ({
      ganho: [],
      total: computed(()=> {
        let temp = 0;

        if (state.ganho.length > 0) {
          for (let i = 0; i < state.ganho.length; i++) {
            temp += state.ganho[i].value
          }
        }

        return temp
      })
    })

    return {
      Header,
      state
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;
}

body {
  background: #EEE;
}

</style>
