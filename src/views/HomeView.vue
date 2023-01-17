<template>
    <div class="container ">
      <div class="row justify-content-between">
        <div class="card col-md-5 col-sm-6 item">
          <h1 class="text-center text-muted">Objetos</h1>
            <form class="row g-3" @submit="incrementarContador">
                <div class="col-12">
                    <span class="text-secundary">Objeto persona completo</span>
                    <label class="text-center text-primary">{{ objPersona }}</label>
                </div>
                <div class="col-auto">
                    <label for="staticEmail2" class="visually-hidden">Salario a modificar</label>
                    <input 
                        type="number" 
                        class="form-control">
                </div>
                <div class="col-auto">
                    <button type="submit" class="btn btn-primary mb-3">Modificar objeto</button>
                </div>
            </form>
        </div>

        <div class="card col-md-5 col-sm-6 item">

          <label>
            texto estático, el contador tiene como valor:
            {{ contador }}
          </label>

            <button @click="incrementarContador">+</button>
            <button @click="decrementarContador">-</button>

            <div class="linea-divisora"></div>

            <span>OBJETO REACTIVO</span>
            <label>Nombre del objeto persona:</label>
            <input 
              type="text" 
              v-model="objPersona.nombre"
            />
            <button @click="mutarEdad">
              mutar/modificar la edad
            </button>

            <div>objeto persona completo:</div>
            <span class="objeto">
              {{ objPersona }}
            </span>
        </div>
      </div>
    </div>
</template>

<script setup>
  // rediniendo característica reactiva de vue
  import { ref, reactive } from 'vue';

  // inicializando constantes
  const contador = ref(0); // <--- solo sirve para tipos primitivos (numeric/Int, String, Boolean...)

  const objPersona = reactive({
    nombre: '',
    edad: '',
    genero: 'f'
  });
  
  // ¿qué pasa si defino un objeto?, ¿Las propiedades de ese objeto siguien siendo reactivas?

  // comportamientos
  const incrementarContador = () => {
    contador.value = contador.value + 1;
    console.log(objPersona)
  }

  const decrementarContador = () => {
    contador.value = contador.value - 1;
    console.log(objPersona)
  }  

  const mutarEdad = () => {
    objPersona.edad = 37;
  }
</script>

<style>
  /* mis reglas CSS o SCSS */
  .linea-divisora {
    color: red;
    border-bottom: 3px solid grey;
    width: 100%;
    height: 5px;
    display: block;    
  }
</style>