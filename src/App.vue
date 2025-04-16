<script setup>
import { useVueToPrint } from 'vue-to-print';
import { ref } from 'vue';

const componentRef = ref();
const { handlePrint } = useVueToPrint({
	content: componentRef,
	documentTitle: 'AwesomeFileName'
});
</script>

<template>
	<div class="componentRef" ref="componentRef">
		<div class="content-box">
			<div class="center">
				<div class="title">Tiendas daka, C.A.</div>

				<div class="center-content">
					<div class="separator">
						<p class="text text-bold">Hasta</p>
						<p class="text text-bold">ANDREINA FABIOLA DIMAS BARRIOS</p>
					</div>

					<div class="separator">
						<p class="text">Fecha</p>
						<p class="text">16/4/2025</p>
					</div>
				</div>
			</div>
		</div>
	</div>

	<button @click="handlePrint">Print</button>
</template>

<style scoped>
.componentRef {
	width: 100%;
	display: flex;
	justify-content: center;
	align-items: center;
}
.content-box {
	border: 1px solid #ccc;
	padding: 20px;
	width: 90%;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
.center {
	display: flex;
	flex-direction: column;
	text-align: center;
	align-items: center;
	justify-content: center;
	width: 100%;
}

/* documents styles */
.title {
	font-size: 25px;
	font-weight: bold;
	color: black;
	text-transform: uppercase;
	text-decoration: underline 4px solid black;
	margin-bottom: 10px;
}
.center-content {
	display: flex;
	justify-content: space-between;
	max-width: 85%;
	width: 100%;
}
.text {
	margin-left: 5px;
	margin-right: 5px;
}
.text-bold {
	font-weight: bold;
}
.separator {
	display: flex;
	margin: 0 10px;
}
</style>
