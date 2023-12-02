
<template>
	 <div class="text-center">
    <!-- Logo and Information Section -->
    <div class="flex items-center justify-center flex-col space-y-4">
      <div class="flex-shrink-0 w-1/3">
        <!-- <img class="w-2/3 h-auto mt-5 mx-auto" src="../../logo2.png" alt="Logo"> -->
      </div>
      <!-- Text below the logo -->
      <h1 class="text-4xl font-bold text-teal-600 mt-2">SIT MOTUL</h1>
      <br>
      <!-- Information Section -->
      <div class="text-center">
        <h2 class="mb-2 text-xl text-gray-700">
          Estado de la evaluación tutor del periodo {{ periodo }} al {{ obtenerFechaActual() }}
        </h2>
      </div>
    </div>

    <!-- Rest of your code... -->
  </div>
		<!-- Tarjetas -->
		<div class="flex justify-center space-x-10 mt-6">
			<!-- Primera columna (tarjeta vertical) -->
			<div class="w-3/2 bg-gradient-to-r from-slate-300 to-gray-200 p-3 rounded-lg"> 
				

				<div v-for="(data, index) in infoGeneral" :key="index"
				 class="bg-blue-900 h-full p-4  rounded-md mb-5 flex items-center justify-center">

					<!-- <a class="mb-2 px-3"><b>Inicio:</b>{{ data.inicio }}</a>
      <a class="mb-2 px-3"><b>Fin:</b>{{ data.fin }}</a> -->
					<!-- Mostrar horas restantes -->
					<div class="mr-4">
        <i class="fas fa-coffee text-5xl text-yellow-500"></i>
    </div>

    <div class="text-center">
        <!-- ... Otro contenido ... -->
        <p class="mb-2 px-3 text-cyan-50 font-bold text-3xl">
            Horas restantes: {{ calcularHorasRestantes(data.fin).horas }}
        </p>

        <p class="mb-2 px-3 text-center text-black font-semibold">para finalizar</p>
        
        <p class="mb-2 px-3 text-cyan-50 font-bold text-3xl">
            Días restantes: {{ calcularHorasRestantes(data.fin).dias }}d <i class="fas fa-calendar-day"></i>
        </p>
        
        <p class="mb-2 px-3 text-center text-black font-semibold">para cerrar</p>
    </div>
</div>
</div>
			<!-- Segunda columna (dos tarjetas una debajo de la otra) -->
			<div class="w-2/6 grid grid-cols-1 gap-2">
				<div v-for="(data, index) in infoGeneral" :key="index"
					class="bg-gradient-to-r from-slate-300 to-gray-200 p-3 rounded-lg mb-5">
					<div class="bg-teal-500 p-4 shadow-md rounded-md">
						<p class="mb-2 px-3 text-cyan-50 font-bold text-3xl">
							{{ calcularPorcentaje(data.alEvaluados, data.alTotal) }} % <i class="fas fa-clipboard-list"></i>
						</p>
						<p class="font-semibold">Hay {{ totalEvaluados }} alumnos que han resuelto la evaluación de un total de {{
							totalAlumnos }} alumnos</p>


					</div>
				</div>

				<div v-for="(data, index) in infoGeneral" :key="index"
					class="bg-gradient-to-r from-slate-300 to-gray-200 p-3 rounded-lg mb-5">
					<div class="bg-sky-500 p-4 shadow-md rounded-md">
						<p class="b-2 px-3 text-cyan-50 font-bold text-3xl">
							{{ calcularPorcentajeFaltante(data.alEvaluados, data.alTotal) }} % <i
								class="fas fa-exclamation-triangle text-red-500"></i>
						</p>
						<p class="font-semibold">
							Alumnos faltantes por evaluar: {{ data.alTotal - data.alEvaluados }} de {{ data.alTotal }}
						</p>
					</div>
				</div>
			</div>
		</div>



		<!-- Información General Section -->
		<div v-if="infoGeneral.length > 0 && infoPersonal.length > 0" class="m-auto w-11/12 mb-5">
			

			<!-- Mostrar tarjetas -->
			<div class="w-12/12 m-auto h-auto rounded-lg bg-gray-50 dark:bg-gray-600 rounded-lg py-8 px-7 mt-10 mb-10">
				<div class="grid grid-cols-2 flex-col space-x-3 mx-3 bg-transparent">
					<!-- Tarjeta de Información Personal -->
					<!-- ... (Rest of your code) -->

					<!-- Tarjeta de Información Personal -->
					<!-- ... (Rest of your code) -->
					<!-- Tarjeta de Información Personal -->
					<div class="w-full mt-2 bg-gradient-to-r from-slate-300 to-gray-200 p-3 rounded-lg mt-2">
						<h1 class="text-2xl text-center font-bold text-black">INGENIERÍA ELECTROMECÁNICA</h1>

						<div v-for="(data, index) in infoPersonal" :key="index" class="bg-white p-4 shadow-md rounded-md">
							<div v-if="data.IEM">
								<p>IEM - Listas: {{ data.IEM.listas }}, Faltantes: {{ data.IEM.faltantes }}</p>
							</div>

							<!-- Otros datos que desees mostrar en la tarjeta -->
						</div>
					</div>

					<!-- Tarjeta de Información Personal -->
					<div class="w-full mt-2 bg-gradient-to-r from-slate-300 to-gray-200 p-3 rounded-lg mt-2">
						<h1 class="text-2xl text-center font-bold text-black">INGENIERÍA EN ENERGÍAS RENOVABLES</h1>

						<div v-for="(data, index) in infoPersonal" :key="index" class="bg-white p-4 shadow-md rounded-md">

							<div v-if="data.IER">
								<p>IER - Listas: {{ data.IER.listas }}, Faltantes: {{ data.IER.faltantes }}</p>
							</div>

							<!-- Otros datos que desees mostrar en la tarjeta -->
						</div>
					</div>
					<!-- Tarjeta de Información Personal -->
					<div class="w-full mt-6 bg-gradient-to-r from-slate-300 to-gray-200 p-3 rounded-lg mt-2">
						<h1 class="text-2xl text-center font-bold text-black">INGENIERÍA INDUSTRIAL </h1>

						<div v-for="(data, index) in infoPersonal" :key="index" class="bg-white p-4 shadow-md rounded-md">

							<div v-if="data.II">
								<p>II - Listas: {{ data.II.listas }}, Faltantes: {{ data.II.faltantes }}</p>
							</div>

							<!-- Otros datos que desees mostrar en la tarjeta -->
						</div>
					</div>
					<!-- Tarjeta de Información Personal -->
					<div class="w-full mt-6 bg-gradient-to-r from-slate-300 to-gray-200 p-3 rounded-lg mt-2">
						<h1 class="text-2xl text-center font-bold text-black">INGENIERÍA EN SISTEMAS</h1>

						<div v-for="(data, index) in infoPersonal" :key="index" class="bg-white p-4 shadow-md rounded-md">


							<div v-if="data.ISC">
								<p>ISC - Listas: {{ data.ISC.listas }}, Faltantes: {{ data.ISC.faltantes }}</p>
							</div>
							<!-- Otros datos que desees mostrar en la tarjeta -->
						</div>
					</div>


				</div>
			</div>
		</div>
		<div v-else>
			<p>No hay datos de alumnos evaluados disponibles.</p>
		</div>
	
</template>

<script setup>
import { onMounted } from 'vue'
import { ref } from 'vue'

// Definir variables reactivas
const infoGeneral = ref([]) // Almacena datos de Información General
const infoPersonal = ref([]) // Almacena datos de Información Personal

// Variables para mostrar en la plantilla
const totalEvaluados = ref(0)
const totalAlumnos = ref(0)
const periodo = ref('')

// Función para obtener datos de la API
async function fetchData(apiUrl, infoArray) {
	try {
		const response = await fetch(apiUrl)
		const data = await response.json()
		infoArray.value.push(data) // Almacenar datos en el array correspondiente

		// Actualizar variables para mostrar en la plantilla
		totalEvaluados.value += data.alEvaluados || 0
		totalAlumnos.value += data.alTotal || 0
		if (!periodo.value) {
			periodo.value = data.periodo || ''
		}

		console.log('Datos recibidos:', data)
		// Imprimir datos adicionales en la consola
		if (data.ObjectIE) {
			console.log('ObjectIE:', data.ObjectIE)
		}
		if (data.IEM) {
			console.log('IEM:', data.IEM)
		}
		if (data.IER) {
			console.log('IER:', data.IER)
		}
		if (data.II) {
			console.log('II:', data.II)
		}
		if (data.ISC) {
			console.log('ISC:', data.ISC)
		}
	} catch (error) {
		console.error('Error al obtener datos:', error)
	}
}

// Función que se ejecuta al montar el componente
onMounted(async () => {
	// Obtener datos de la primera API
	await fetchData('https://sitmotul.com.mx/api/statusEval', infoGeneral)

	// Obtener datos de la segunda API (puedes cambiar la URL según sea necesario)
	await fetchData('https://sitmotul.com.mx/api/statusEvalIng', infoPersonal)
})

// Función para calcular las horas y días restantes hasta la fecha y hora indicada
const calcularHorasRestantes = (fechaFin) => {
	const ahora = new Date();
	const fechaFinalizacion = new Date(fechaFin);
	const diferenciaTiempo = fechaFinalizacion - ahora;

	const diferenciaDias = Math.floor(diferenciaTiempo / (1000 * 60 * 60 * 24));
	const diferenciaHoras = Math.floor(diferenciaTiempo / (1000 * 60 * 60));

	return {
		dias: diferenciaDias >= 0 ? diferenciaDias : 0,
		horas: diferenciaHoras >= 0 ? diferenciaHoras : 0,
	};
};

// Función para calcular el porcentaje
const calcularPorcentaje = (evaluados, total) => {
	if (total === 0) {
		return 0;
	}
	return ((evaluados / total) * 100).toFixed(2);
};

// Función para calcular el porcentaje de los evaluados que faltan
const calcularPorcentajeFaltante = (evaluados, total) => {
	const faltantes = total - evaluados;
	if (total === 0 || faltantes <= 0) {
		return 0;
	}
	return ((faltantes / total) * 100).toFixed(2);
};



// Función para obtener la fecha actual en el formato deseado
const obtenerFechaActual = () => {
	const opcionesFecha = {
		weekday: "long",
		day: "numeric",
		month: "long",
		year: "numeric",
	};
	const fechaActual = new Date();
	return fechaActual.toLocaleDateString("es-MX", opcionesFecha);
};
</script>
		