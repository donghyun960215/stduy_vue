<template>
  <ul>
    <Fruit
      v-for="fruit in fruits"
      :key="fruit"
      :name="fruit">
      {{ fruit }}
    </Fruit>
  </ul>
</template>

<script>

import Fruit from '~/components/Fruit';

export default {
  components: {
    Fruit
  },
  data() {
    return{
      fruits: ['Apple','Banana','cherry']
    }
  }
}
</script>

<style lang = "scss">
  h1{
    font-size: 50px;
    color: red;
  }
  ul {
    li{
      font-size: 40px;
    }
  }
</style>