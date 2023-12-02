
<template>
  <div id="app">
    <h1>Math Quiz App</h1>
    {{ operator }}
    <OperatorSelector @changeOperator="changeOperator"/>
  </div>
</template>

<script>
import OperatorSelector from './components/OperatorSelector.vue'
export default {
    name: "app",
    data() {
        return {
            operator: null
        };
    },
    methods: {
        changeOperator(operator) {
            this.operator = operator;
        }
    },
    components: {OperatorSelector }
}
</script>

<style scoped>
#app {
  text-align: center;
  margin-top: 60px;
  font-size: 24px;
}

button {
  padding: 10px;
  width: 160px;
  cursor: pointer;
}
</style>
