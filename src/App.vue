<script setup>
import { ref } from 'vue';

const contador = ref(0)
const numero = ref(1)
const incrementar = (() => {
 if((contador.value+numero.value) > 10){
  contador.value = 10
 }else if ( contador.value <= 10){
    contador.value+=numero.value
  }
})
const decrementar = (() => {
if((contador.value-numero.value) < 0){
  contador.value = 0
 }else if ( contador.value >= 0){
    contador.value-=numero.value
  }
})
</script>
<template>
  <main>
    <div><h1>contador: {{ contador }}</h1></div>
    <div class="branco">Valor a incrementar/decrementar:<input type="number" v-model="numero" :max="10" :min="1"></div>
    <div class="div-btn">
      <button class="btn" @click="incrementar" :disabled="contador>=10">
        incrementar
      </button>
      <button class="btn" @click="decrementar" :disabled="contador<=0">
        decrementar
      </button>
    </div>
    <div class="bah" v-if="contador >= 10 || contador <= 0">
      <p v-if="contador === 10">contador está no máximo</p>
      <p v-else-if="contador === 0">contador está no minimo</p>
    </div>
  </main>
</template>
<style scoped>
.branco{
  color: white;
}
h1{
  color: white;
}
.div-btn{
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20px;
  margin-top: 10px;
}
.bah{
  background-color: red;
  color: white;
}
.btn{
  color: white;
  background-color: rgb(72, 194, 72);
  padding: 10px 34px;
  border: none ;
  border-radius:10px ;
  transition: all 1s ease;

}
.btn:hover{
transform: scale(1.05);
background-color: rgb(66, 151, 66);
}

</style>