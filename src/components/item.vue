<template>
  <div class="item">
    <div class="removeItem" @click="removeItem">x</div>
    <div class="desc">{{ quantia.desc }}</div>
    <div class="value">R${{ quantia.value }}</div>
    <div class="date">{{ formattedDate }}</div>
  </div>
</template>

<script>
export default {
  name: 'Item',
  props: {
    quantia: Object,
  },
  setup(props, {emit}) {
    let date = new Date(props.quantia.date);
    let dia = date.getDate();
    let mes = date.getMonth();
    let ano = date.getFullYear();

    let formattedDate = dia + '/' + mes + '/' + ano;

    function removeItem() {
      emit('remove-item', props.quantia.id);
    };

    return {
      formattedDate,
      removeItem,
    };
  }
}
</script>

<style scoped>
  .item {
    position: relative;
    display: flex;
    padding: 15px 15px 15px 0px;
    background-color: #FFF;
    border-radius: 8px;
    max-width: 600px;
    margin: 0 auto 30px;
  }
  .removeItem {
    color: #EF2D2D;
    font-weight: 600;
    font-size: 20px;
    line-height: 1;
    text-align: center;
    margin: 0 15px;
    cursor: pointer;
  }
  .desc {
    color: #666;
    flex: 1 1 100%;
    font-size: 20px;
  }
  .value {
    color: #666;
    min-width: 100px;
    font-size: 20px;
  }
  .date {
    color: #666;
    text-align: right;
    font-size: 20px;
  }
</style>