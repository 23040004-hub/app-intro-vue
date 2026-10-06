<script>
export default {
  name: 'EjemplosVue',

  data() {
    return {
      mensaje: 'Hola desde Vue.js',
      esVisible: true,

      nombre: '',

      contador: 0,

      tecnologias: [
        { id: 1, nombre: 'HTML' },
        { id: 2, nombre: 'CSS' },
        { id: 3, nombre: 'JavaScript' },
        { id: 4, nombre: 'Vue.js' },
      ],

      resaltado: false,
    }
  },

  computed: {
    mensajeNombre() {
      if (this.nombre === '') {
        return 'Escribe tu nombre para comenzar'
      }

      return `Hola ${this.nombre}, estás aprendiendo Vue.js`
    },

    dobleContador() {
      return this.contador * 2
    },
  },

  methods: {
    cambiarVisibilidad() {
      this.esVisible = !this.esVisible
    },

    aumentarContador() {
      this.contador++
    },

    disminuirContador() {
      if (this.contador > 0) {
        this.contador--
      }
    },

    cambiarResaltado() {
      this.resaltado = !this.resaltado
    },

    mostrarSaludo() {
      alert('¡Hola! Este evento fue ejecutado con Vue.js')
    },
  },
}
</script>

<template>
  <section class="contenedor">

    <div class="titulo-principal">
      <span>PRÁCTICA</span>
      <h2>Introducción a Vue.js</h2>
      <p>
        Ejemplos de los conceptos principales utilizados en Vue.
      </p>
    </div>

    <div class="cuadricula">

      <!-- V-IF -->
      <div class="tarjeta">
        <div class="encabezado-tarjeta">
          <span class="numero">01</span>
          <div>
            <h3>Renderizado condicional</h3>
            <p>Directiva v-if</p>
          </div>
        </div>

        <div class="ejemplo">
          <h4 v-if="esVisible">
            {{ mensaje }}
          </h4>

          <p v-else class="oculto">
            El mensaje está oculto
          </p>
        </div>

        <button @click="cambiarVisibilidad">
          {{ esVisible ? 'Ocultar mensaje' : 'Mostrar mensaje' }}
        </button>
      </div>


      <!-- V-MODEL -->
      <div class="tarjeta">
        <div class="encabezado-tarjeta">
          <span class="numero">02</span>
          <div>
            <h3>Enlace de datos</h3>
            <p>Directiva v-model</p>
          </div>
        </div>

        <label>Escribe tu nombre</label>

        <input
          v-model="nombre"
          type="text"
          placeholder="Tu nombre..."
        />

        <div class="resultado">
          {{ mensajeNombre }}
        </div>
      </div>


      <!-- EVENTOS -->
      <div class="tarjeta">
        <div class="encabezado-tarjeta">
          <span class="numero">03</span>
          <div>
            <h3>Eventos</h3>
            <p>v-on / @click</p>
          </div>
        </div>

        <div class="contador">
          {{ contador }}
        </div>

        <div class="botones-contador">
          <button @click="disminuirContador">
            − Disminuir
          </button>

          <button @click="aumentarContador">
            + Aumentar
          </button>
        </div>

        <button
          class="boton-secundario"
          @click="mostrarSaludo"
        >
          Mostrar alerta
        </button>
      </div>


      <!-- V-FOR -->
      <div class="tarjeta">
        <div class="encabezado-tarjeta">
          <span class="numero">04</span>
          <div>
            <h3>Renderizado de listas</h3>
            <p>Directiva v-for</p>
          </div>
        </div>

        <ul class="lista">
          <li
            v-for="tecnologia in tecnologias"
            :key="tecnologia.id"
          >
            <span>✓</span>
            {{ tecnologia.nombre }}
          </li>
        </ul>
      </div>


      <!-- V-BIND -->
      <div class="tarjeta">
        <div class="encabezado-tarjeta">
          <span class="numero">05</span>
          <div>
            <h3>Atributos dinámicos</h3>
            <p>Directiva v-bind</p>
          </div>
        </div>

        <h4
          class="texto-bind"
          :class="{ resaltado: resaltado }"
        >
          Vue.js permite modificar estilos dinámicamente
        </h4>

        <button @click="cambiarResaltado">
          Cambiar estilo
        </button>
      </div>


      <!-- COMPUTED -->
      <div class="tarjeta">
        <div class="encabezado-tarjeta">
          <span class="numero">06</span>
          <div>
            <h3>Propiedades computadas</h3>
            <p>Computed properties</p>
          </div>
        </div>

        <div class="datos-computed">
          <div>
            <span>Contador</span>
            <strong>{{ contador }}</strong>
          </div>

          <div>
            <span>Valor doble</span>
            <strong>{{ dobleContador }}</strong>
          </div>
        </div>

        <p class="explicacion">
          El valor doble se calcula automáticamente cuando cambia
          el contador.
        </p>
      </div>

    </div>

  </section>
</template>

<style scoped>
.contenedor {
  width: 100%;
}

.titulo-principal {
  margin-bottom: 25px;
}

.titulo-principal > span {
  color: #2563eb;
  font-size: 11px;
  font-weight: bold;
  letter-spacing: 1.5px;
}

.titulo-principal h2 {
  font-size: 28px;
  margin-top: 5px;
  margin-bottom: 6px;
}

.titulo-principal p {
  color: #64748b;
  font-size: 13px;
}

.cuadricula {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 18px;
}

.tarjeta {
  background-color: white;
  border: 1px solid #e2e8f0;
  border-radius: 14px;
  padding: 22px;

  transition: 0.2s;
}

.tarjeta:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.06);
}

.encabezado-tarjeta {
  display: flex;
  align-items: center;
  gap: 12px;

  margin-bottom: 20px;
}

.numero {
  width: 38px;
  height: 38px;

  display: flex;
  align-items: center;
  justify-content: center;

  border-radius: 9px;

  background-color: #eff6ff;
  color: #2563eb;

  font-size: 12px;
  font-weight: bold;
}

.encabezado-tarjeta h3 {
  font-size: 15px;
  margin-bottom: 3px;
}

.encabezado-tarjeta p {
  color: #94a3b8;
  font-size: 11px;
}

.ejemplo {
  min-height: 60px;

  display: flex;
  align-items: center;

  background-color: #f8fafc;
  border-radius: 8px;

  padding: 12px;

  margin-bottom: 12px;
}

.ejemplo h4 {
  color: #2563eb;
}

.oculto {
  color: #94a3b8;
}

label {
  display: block;
  font-size: 12px;
  font-weight: bold;

  margin-bottom: 7px;
}

input {
  width: 100%;

  border: 1px solid #cbd5e1;
  border-radius: 8px;

  padding: 10px 12px;

  outline: none;
}

input:focus {
  border-color: #2563eb;
}

.resultado {
  margin-top: 12px;

  padding: 12px;

  background-color: #eff6ff;
  color: #2563eb;

  border-radius: 8px;

  font-size: 13px;
}

button {
  border: none;

  background-color: #2563eb;
  color: white;

  border-radius: 7px;

  padding: 9px 14px;

  font-size: 12px;

  transition: 0.2s;
}

button:hover {
  background-color: #1d4ed8;
}

.contador {
  font-size: 35px;
  font-weight: bold;

  text-align: center;

  margin: 15px 0;
}

.botones-contador {
  display: flex;
  gap: 8px;
}

.botones-contador button {
  flex: 1;
}

.boton-secundario {
  width: 100%;

  margin-top: 8px;

  background-color: #f1f5f9;
  color: #475569;
}

.boton-secundario:hover {
  background-color: #e2e8f0;
}

.lista {
  list-style: none;

  display: flex;
  flex-direction: column;

  gap: 8px;
}

.lista li {
  background-color: #f8fafc;

  padding: 10px;

  border-radius: 7px;

  font-size: 13px;
}

.lista li span {
  color: #16a34a;
  margin-right: 8px;
}

.texto-bind {
  padding: 18px;

  background-color: #f8fafc;

  border-radius: 8px;

  margin-bottom: 12px;

  transition: 0.3s;
}

.texto-bind.resaltado {
  background-color: #fef3c7;
  color: #b45309;
}

.datos-computed {
  display: grid;
  grid-template-columns: repeat(2, 1fr);

  gap: 10px;
}

.datos-computed div {
  background-color: #f8fafc;

  border-radius: 8px;

  padding: 15px;

  text-align: center;

  display: flex;
  flex-direction: column;

  gap: 5px;
}

.datos-computed span {
  color: #64748b;
  font-size: 11px;
}

.datos-computed strong {
  color: #2563eb;
  font-size: 22px;
}

.explicacion {
  color: #64748b;

  font-size: 11px;
  line-height: 1.5;

  margin-top: 12px;
}

@media (max-width: 900px) {
  .cuadricula {
    grid-template-columns: 1fr;
  }
}
</style>