<template>
  <div>
    <Header :totalSobra="state.total" />
    <Form @add-value="addValue" />
  </div>
</template>

<script>
import Header from './components/header.vue'
import {reactive, computed} from 'vue'
import Form from './components/form.vue'

export default {
  name: 'App',
  components: {
    Header,
    Form,
  },
  setup() {

    const state = reactive ({
      ganho: [],
      total: computed(()=> {
        let temp = 0;

        if (state.ganho.length > 0) {
          for (let i = 0; i < state.ganho.length; i++) {
            if(state.ganho[i].ganho_gasto == "1") {
              temp += state.ganho[i].value
            } else {
              temp -= state.ganho[i].value
            }
          }
        }

        return temp
      })
    });

    function addValue(data) {

      let d = data.date.split('-');
      let newD = new Date(d[0], d[1], d[2])

      state.ganho = [...state.ganho, {
        id: Date.now(),
        desc: data.desc,
        value: data.value,
        date: newD.getTime(),
        ganho_gasto: data.type,
      }];

      console.log(state.ganho)
    }

    return {
      Header,
      state,
      Form,
      addValue,
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
