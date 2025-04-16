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
  <div class="componentRef" ref="componentRef">
   <div class="center">
   <div class="title">
    Tiendas daka, C.A.
   </div>

   <div class="center-content">
    <p class="text text-bold">Hasta</p>
    <p class="text text-bold">ANDREINA FABIOLA DIMAS BARRIOS</p>
    <p class="text">Fecha</p>
    <p class="text">16/4/2025</p>
   </div>
   </div>
  </div>

  <button @click="handlePrint">Print</button>
</template>

<style scoped>
.componentRef {
  width: 100%;
  display: flex;
}
.center {
  display: flex;
  flex-direction: column;
  text-align: center;
  width: 100%;
  align-self: flex-start;
}

/* documents styles */
.title {
  font-size: 32.5px;
  font-weight: bold;
  color:black;
  text-transform: uppercase;
  text-decoration: underline 4px solid black;
}
.center-content {
  display: flex;
  justify-content: center;
  }
  .text {
    margin-left: 10px;
    margin-right: 10px;
  }
  .text-bold {
    font-weight: bold;
  }
</style>