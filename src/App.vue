<script setup>
import { useVueToPrint } from "vue-to-print";
import { ref } from "vue";

const componentRef = ref();
const { handlePrint } = useVueToPrint({
  content: componentRef,
  documentTitle: "AwesomeFileName",
});
</script>

<template>
  <button @click="handlePrint">Print</button>
  <div class="componentRef" ref="componentRef">
   <div class="center">
    <h1>Print pdf</h1>
   </div>
  </div>
</template>

<style scoped>
.componentRef {
  width: 100%;
  display: flex;
  justify-content: center;
}
.center {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  width: 100%;
}
</style>