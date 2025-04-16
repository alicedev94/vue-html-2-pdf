<script setup>
import { useVueToPrint } from 'vue-to-print';
import { ref } from 'vue';

const componentRef = ref();
const { handlePrint } = useVueToPrint({
	content: componentRef,
	documentTitle: 'SAP_B1_Comprobante'
});
</script>

<template>
	<div class="componentRef" ref="componentRef">
		<div class="content-box">
			<div class="sap-document">
				<!-- Encabezado: Nombre empresa centrado con línea debajo -->
				<div class="header-row">
					<div class="header-item">Tiendas daka, C.A.</div>
				</div>

				<!-- Línea 1: "Hasta" con nombre y fecha con space-between -->
				<div class="info-row">
					<div class="hasta-section">
						<span class="label">Hasta</span>
						<span class="value client-name">ANDREINA FABIOLA DIMAS BARRIOS</span>
					</div>
					<div class="fecha-section">
						<span class="label">Fecha</span>
						<span class="value">18/04/2025</span>
					</div>
				</div>

				<!-- Línea 2: Número de identificación alineado a la derecha -->
				<div class="identificacion-row">
					<div></div>
					<div class="id-section">
						<span class="label">Número de identificación</span>
						<span class="value">J-0000000-1</span>
					</div>
				</div>

				<!-- Línea 3: Recibo, número, original (centrado) -->
				<div class="receipt-section">
					<div class="receipt-item">Recibo</div>
					<div class="receipt-item">5613316</div>
					<div class="receipt-item">Original</div>
				</div>

				<!-- Línea 4: Fondos en efectivo y monto (alineado derecha) -->
				<div class="payment-row fondos">
					<div class="payment-label">Fondos en efectivo</div>
					<div class="payment-box">
						<span class="currency">Bs</span>
						<span class="amount">1.000,00</span>
					</div>
				</div>

				<!-- Línea 5: Autor manager (izquierda) -->
				<div class="author-row">
					<div class="author-label">Autor: Manager</div>
					<div></div>
					<!-- Espacio vacío para alineación -->
				</div>

				<!-- Línea 6: Comentario y Pago a cuenta (con space-between) -->
				<div class="payment-row comments">
					<div class="comments-section">
						<span class="label">Comentarios</span>
						<span class="value">Comentarios del operador</span>
					</div>
					<div class="payment-account">
						<div class="payment-label">Pago a cuenta</div>
						<div class="payment-box">
							<span class="amount">1.000,00</span>
						</div>
					</div>
				</div>

				<!-- Línea 7: Firma (izquierda) y Total (derecha) -->
				<div class="signature-total-row">
					<div class="signature-section">
						<span class="label">Firma</span>
						<div class="signature-line"></div>
					</div>
					<div class="total-section">
						<span class="total-label">Total</span>
						<div class="total-box">
							<span class="currency">Bs</span>
							<span class="amount">1.000,00</span>
						</div>
					</div>
				</div>

				<!-- Pie de página -->
				<div class="sap-footer">
					<div class="footer-contact">
						<p>Teléfono: (0212) 555-5555</p>
						<p>Dirección: Av. Principal, Edif. Central, Caracas, Venezuela</p>
					</div>
				</div>
			</div>
		</div>
	</div>

	<div class="print-controls">
		<button class="print-button" @click="handlePrint">Imprimir Comprobante</button>
	</div>
</template>

<style scoped>
.componentRef {
	width: 100%;
	display: flex;
	justify-content: center;
	padding: 20px 0;
	font-family: Arial, Helvetica, sans-serif;
}

.content-box {
	border: 1px solid #ccc;
	padding: 20px;
	width: 790px;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	background-color: white;
}

.sap-document {
	display: flex;
	flex-direction: column;
	width: 100%;
}

/* Header */
.header-row {
	display: flex;
	justify-content: center;
	padding-bottom: 15px;
	margin-bottom: 20px;
	border-bottom: 2px solid #000;
}

.header-item {
	font-size: 24px;
	font-weight: bold;
	text-transform: uppercase;
	text-decoration: underline;
	text-align: center;
}

/* Información cliente */
.info-row {
	display: flex;
	justify-content: space-between;
	margin-bottom: 10px;
}

.hasta-section,
.fecha-section {
	display: flex;
	align-items: center;
}

.label {
	font-weight: bold;
	margin-right: 10px;
}

.value {
	margin-right: 5px;
}

.client-name {
	font-weight: bold;
}

/* Número de identificación */
.identificacion-row {
	display: flex;
	justify-content: space-between;
	margin-bottom: 10px;
}

.id-section {
	display: flex;
	align-items: center;
}

/* Recibo */
.receipt-section {
	display: flex;
	justify-content: center;
	margin: 25px 0;
}

.receipt-item {
	font-size: 22px;
	font-weight: bold;
	margin: 0 15px;
}

/* Fondos en efectivo */
.payment-row {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin-bottom: 10px;
}

.fondos {
	margin-bottom: 15px;
}

.payment-label {
	font-weight: bold;
}

.payment-box {
	border: 1px solid #000;
	padding: 8px 15px;
	min-width: 150px;
	text-align: right;
}

/* Autor */
.author-row {
	display: flex;
	justify-content: space-between;
	margin-bottom: 10px;
}

.author-label {
	font-weight: bold;
}

/* Comentarios y pago a cuenta */
.comments {
	margin-bottom: 25px;
}

.comments-section {
	display: flex;
	align-items: center;
}

.payment-account {
	display: flex;
	align-items: center;
}

.payment-account .payment-label {
	margin-right: 10px;
}

/* Firma y Total */
.signature-total-row {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin-bottom: 30px;
}

.signature-section {
	display: flex;
	align-items: center;
}

.signature-line {
	border-bottom: 1px solid #000;
	width: 200px;
	height: 1px;
	margin-left: 5px;
}

.total-section {
	display: flex;
	align-items: center;
}

.total-label {
	font-weight: bold;
	margin-right: 10px;
}

.total-box {
	border: 1px solid #000;
	padding: 8px 15px;
	min-width: 150px;
	text-align: right;
}

.currency {
	margin-right: 5px;
}

.amount {
	font-weight: bold;
}

/* Footer */
.sap-footer {
	margin-top: 30px;
	padding-top: 15px;
	border-top: 1px solid #ddd;
	text-align: center;
}

.footer-contact p {
	margin: 3px 0;
	font-size: 12px;
}

/* Print Controls */
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
