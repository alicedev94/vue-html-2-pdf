<script setup>
/*
 * Componente del comprobante imprimible de SAP B1
 * Recibe los datos mediante props desde el componente padre
 */
import { defineProps } from 'vue';

// Definición de props del componente
const props = defineProps({
	comprobanteData: {
		type: Object,
		required: true
	}
});
</script>

<template>
	<!-- Contenedor principal que será impreso -->
	<div class="comprobante-container">
		<div class="comprobante-content">
			<div class="sap-documento">
				<!-- Encabezado: Nombre empresa centrado con subrayado -->
				<div class="header-row">
					<div class="header-item">{{ comprobanteData.empresa.nombre }}</div>
				</div>

				<!-- Sección de información del cliente y fecha -->
				<div class="info-row">
					<!-- Sección destinatario -->
					<div class="hasta-section">
						<span class="label">Hasta</span>
						<span class="value client-name">{{ comprobanteData.cliente.nombre }}</span>
					</div>
					<!-- Sección fecha -->
					<div class="fecha-section">
						<span class="label-2">Fecha</span>
						<span class="label-2 value">{{ comprobanteData.comprobante.fecha }}</span>
					</div>
				</div>

				<!-- Sección de identificación fiscal -->
				<div class="identificacion-row">
					<div></div>
					<div class="id-section">
						<span class="label-2">Número de identificación</span>
						<span class="label-2 value"
							>{{ comprobanteData.cliente.identificacion.tipo }}-{{
								comprobanteData.cliente.identificacion.numero
							}}</span
						>
					</div>
				</div>

				<!-- Sección de información del recibo -->
				<div class="receipt-section">
					<div class="receipt-item">Recibo</div>
					<div class="receipt-item">{{ comprobanteData.comprobante.numero }}</div>
					<div class="receipt-item">{{ comprobanteData.comprobante.tipo }}</div>
				</div>

				<!-- Sección de información de pago en efectivo -->
				<div class="payment-row fondos">
					<div class="payment-label">Fondos en efectivo</div>
					<div class="payment-box">
						<span class="currency">{{ comprobanteData.transaccion.fondosEfectivo.moneda }}</span>
						<span class="amount">{{ comprobanteData.transaccion.fondosEfectivo.monto }}</span>
					</div>
				</div>

				<!-- Sección de autorización -->
				<div class="author-row">
					<div class="author-label">Autor: {{ comprobanteData.operacion.autor }}</div>
					<div></div>
					<!-- Espacio vacío para alineación -->
				</div>

				<!-- Sección de comentarios y pago a cuenta -->
				<div class="payment-row comments">
					<div class="comments-section">
						<span class="label">Comentarios</span>
						<span class="value">{{ comprobanteData.operacion.comentarios }}</span>
					</div>
					<div class="payment-account">
						<div class="payment-label">Pago a cuenta</div>
						<div class="payment-box">
							<span class="amount">{{ comprobanteData.transaccion.pagoACuenta.monto }}</span>
						</div>
					</div>
				</div>

				<!-- Sección de firma y total -->
				<div class="signature-total-row">
					<div class="signature-section">
						<span class="label">Firma</span>
						<div class="signature-line"></div>
					</div>
					<div class="total-section">
						<span class="total-label">Total</span>
						<div class="total-box">
							<span class="currency">{{ comprobanteData.transaccion.total.moneda }}</span>
							<span class="amount">{{ comprobanteData.transaccion.total.monto }}</span>
						</div>
					</div>
				</div>

				<!-- Pie de página con información de contacto -->
				<div class="sap-footer">
					<div class="footer-contact">
						<p>Dirección: {{ comprobanteData.empresa.direccion }}</p>
						<p>Teléfono: {{ comprobanteData.empresa.telefono }}</p>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<style scoped>
/* Estilos para el contenedor principal del comprobante */
.comprobante-container {
	width: 100%;
	display: flex;
	justify-content: center;
	padding: 20px 0;
	font-family: Arial, Helvetica, sans-serif;
}

/* Caja de contenido con borde y sombra */
.comprobante-content {
	border: 1px solid #ccc;
	padding: 20px;
	width: 790px;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	background-color: white;
}

/* Contenedor del documento SAP */
.sap-documento {
	display: flex;
	flex-direction: column;
	width: 100%;
}

/* Estilos de encabezado */
.header-row {
	display: flex;
	justify-content: center;
	padding-bottom: 15px;
	margin-top: 20px;
	margin-bottom: 20px;
}

.header-item {
	font-size: 24px;
	font-weight: bold;
	text-transform: uppercase;
	text-decoration: underline;
	text-align: center;
}

/* Estilos para información del cliente */
.info-row {
	display: flex;
	justify-content: space-between;
	margin-top: 30px;
	margin-bottom: 10px;
}

.hasta-section,
.fecha-section {
	display: flex;
	align-items: center;
}

/* Etiquetas estándar */
.label {
	font-weight: bold;
	margin-right: 10px;
}

/* Etiquetas con tamaño más pequeño */
.label-2 {
	font-size: small;
	font-weight: bold;
	margin-right: 10px;
}

/* Valores generales */
.value {
	margin-right: 5px;
}

/* Nombre del cliente con énfasis */
.client-name {
	font-weight: bold;
}

/* Estilos para sección de identificación */
.identificacion-row {
	display: flex;
	justify-content: space-between;
	margin-bottom: 10px;
}

.id-section {
	display: flex;
	align-items: center;
}

/* Estilos para sección de recibo */
.receipt-section {
	display: flex;
	justify-content: center;
	margin-top: 70px;
	margin-bottom: 180px;
}

.receipt-item {
	font-size: 22px;
	font-weight: bold;
	margin: 0 15px;
}

/* Estilos para filas de pago */
.payment-row {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin-bottom: 10px;
}

/* Espacio adicional para fondos en efectivo */
.fondos {
	margin-bottom: 15px;
}

.payment-label {
	font-weight: bold;
}

/* Caja para mostrar montos */
.payment-box {
	border: 1px solid #000;
	padding: 8px 15px;
	min-width: 150px;
	text-align: right;
}

/* Estilos para sección de autor */
.author-row {
	display: flex;
	justify-content: space-between;
	margin-bottom: 10px;
}

.author-label {
	font-weight: bold;
}

/* Estilos para comentarios y pago a cuenta */
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

/* Estilos para firma y total */
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

/* Estilos para pie de página */
.sap-footer {
	margin-top: 30px;
	padding-top: 15px;
	border-top: 1px solid #ddd;
	text-align: center;
}

/* Distribución de información de contacto */
.footer-contact {
	display: flex;
	justify-content: space-between;
}

.footer-contact p {
	margin: 3px 0;
	font-size: 12px;
}
</style>
