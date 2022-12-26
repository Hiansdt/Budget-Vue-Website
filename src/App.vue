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
      ganho: [{
        ganho_gasto: 0,
        value: 200
      },
    {
      ganho_gasto: 1,
      value: 600,
    }],
      total: computed(()=> {
        let temp = 0;

        if (state.ganho.length > 0) {
          for (let i = 0; i < state.ganho.length; i++) {
            if(state.ganho[i].ganho_gasto == 1) {
              temp += state.ganho[i].value
            } else {
              temp -= state.ganho[i].value
            }
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
