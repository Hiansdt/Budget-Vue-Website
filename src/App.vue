<template>
  <div>
    <Header :totalSobra="state.total" />
    <Form @add-value="addValue" />
    <Lista :state="state" @remove="delItem"/>
  </div>
</template>

<script>
import Header from './components/header.vue'
import {reactive, computed} from 'vue'
import Form from './components/form.vue'
import Lista from './components/Lista.vue'

export default {
  name: 'App',
  components: {
    Header,
    Form,
    Lista,
  },
  setup() {

    const state = reactive ({
      quantia: [],
      total: computed(()=> {
        let temp = 0;

        if (state.quantia.length > 0) {
          
          for (let i = 0; i < state.quantia.length; i++) {
            if(state.quantia[i].ganho_gasto == "1") {
              temp += state.quantia[i].value
            } else {
              temp -= state.quantia[i].value
            }
          }
        }

        return temp
      }),
      quantiaOrganizada: computed(() => {
        let temp = [];
        
        temp = state.quantia.sort(function(a, b) {
          return b.date - a.date;
        })

        return temp;
      })
    });

    if (JSON.parse(localStorage.getItem('quant'))) {
      state.quantia = (JSON.parse(localStorage.getItem('quant')))
    }

    function addValue(data) {

      let d = data.date.split('-');
      let newD = new Date(d[0], d[1], d[2])

      state.quantia = [...state.quantia, {
        id: Date.now(),
        desc: data.desc,
        value: data.value,
        date: newD.getTime(),
        ganho_gasto: data.type,
      }];

        localStorage.setItem('quant', JSON.stringify(state.quantia));
    }

    function delItem(id) {
      state.quantia = state.quantia.filter(v => v.id != id);
      localStorage.setItem('quant', JSON.stringify(state.quantia));
    };

    return {
      Header,
      state,
      Form,
      addValue,
      Lista,
      delItem,
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
