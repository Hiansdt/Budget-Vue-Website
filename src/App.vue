<template>
  <div>
    <seletor @selecionar="seletor=$event" />
    <janeiro v-if="seletor==1" />
    <fevereiro v-if="seletor==2" />
    <março v-if="seletor==3"/>
    <abril v-if="seletor==4"/>
    <maio v-if="seletor==5"/>
    <junho v-if="seletor==6"/>
    <julho v-if="seletor==7"/>
    <agosto v-if="seletor==8"/>
    <setembro v-if="seletor==9"/>
    <outubro v-if="seletor==10"/>
    <novembro v-if="seletor==11"/>
    <dezembro v-if="seletor==12"/>
    {{ seletor }}
  </div>
</template>

<script>
import seletor from './components/seletor.vue'
import janeiro from './components/janeiro.vue'
import fevereiro from './components/fevereiro.vue'
import março from './components/março.vue'
import abril from './components/abril.vue'
import maio from './components/maio.vue'
import junho from './components/junho.vue'
import julho from './components/julho.vue'
import agosto from './components/agosto.vue'
import setembro from './components/setembro.vue'
import outubro from './components/outubro.vue'
import novembro from './components/novembro.vue'
import dezembro from './components/dezembro.vue'


export default {
  name: 'App',
  components: {
    janeiro,
    seletor,
    fevereiro,
    março,
    abril,
    maio,
    junho,
    julho,
    agosto,
    setembro,
    outubro,
    novembro,
    dezembro,
  },
  data() {
    return {
      seletor: 1
    }
  }
}
</script>

<style>
</style>
