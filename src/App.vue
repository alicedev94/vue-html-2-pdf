<script setup>
/*
 * Configuración del componente de impresión
 * Utiliza vue-to-print para generar un comprobante imprimible de SAP B1
 */
import { useVueToPrint } from 'vue-to-print';
import { ref } from 'vue';
import ComprobanteImprimible from './components/ComprobanteImprimible.vue';

// Referencia al componente que será impreso
const componentRef = ref();

// Datos del comprobante en formato JSON estático
const comprobanteData = {
	empresa: {
		nombre: 'Tiendas daka, C.A.',
		direccion: 'Av. Principal, Edif. Central, Caracas, Venezuela',
		telefono: '(0212) 555-5555'
	},
	cliente: {
		nombre: 'ANDREINA FABIOLA DIMAS BARRIOS',
		identificacion: {
			tipo: 'J',
			numero: '0000000-1'
		}
	},
	comprobante: {
		fecha: '18/04/2025',
		numero: '5613316',
		tipo: 'Original'
	},
	transaccion: {
		fondosEfectivo: {
			moneda: 'Bs',
			monto: '1.000,00'
		},
		pagoACuenta: {
			monto: '1.000,00'
		},
		total: {
			moneda: 'Bs',
			monto: '1.000,00'
		}
	},
	operacion: {
		autor: 'Manager',
		comentarios: 'Comentarios del operador'
	}
};

// Configuración del hook de impresión
const { handlePrint } = useVueToPrint({
	content: componentRef,
	documentTitle: 'SAP_B1_Comprobante'
});
</script>

<template>
	<!-- Componente modularizado con datos pasados por props -->
	<ComprobanteImprimible ref="componentRef" :comprobante-data="comprobanteData" />

	<!-- Controles de impresión (no aparecen en la versión impresa) -->
	<div class="print-controls">
		<button class="print-button" @click="handlePrint">Imprimir Comprobante</button>
	</div>
</template>

<style scoped>
/* Estilos para controles de impresión */
.print-controls {
	display: flex;
	justify-content: center;
	margin-top: 20px;
}

.print-button {
	background-color: #0066b3;
	color: white;
	border: none;
	padding: 10px 20px;
	border-radius: 4px;
	cursor: pointer;
	font-size: 16px;
}

.print-button:hover {
	background-color: #004b84;
}
</style>
