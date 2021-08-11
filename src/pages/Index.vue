<template>
  <q-page class="flex flex-center">

    <Message v-show="state.result" :result="state.message" />

    <q-form
    align="center"
    @submit="Calcular"
    @reset="Reset"
    class="q-gutter-lg"
    style="width: 300px"
    >
      <img src="../assets/bomba.svg"/>

      <q-input
        outlined
        v-model.number="state.alcool"
        type="number"
        class="tel"
        step="0.01"
        min="0.01"
        prefix="R$"
        label-slot
      >
        <template v-slot:label>
          <span class="text-weight-bold">Valor do Álcool</span>
        </template>
      </q-input>

      <q-input
        outlined
        v-model.number="state.gasolina"
        type="number"
        class="tel"
        step="0.01"
        min="0.01"
        prefix="R$"
        label-slot
      >
        <template v-slot:label>
          <span class="text-weight-bold">Valor da Gasolina</span>
        </template>
      </q-input>

      <div>
        <q-btn label="Calcular" type="submit" color="primary" />
        <q-btn label="Limpar" type="reset" flat color="q-ml-sm" />
      </div>
    </q-form>
  </q-page>
</template>

<script>
import { defineComponent, ref, reactive } from 'vue';
import Message from '../components/Message.vue'

export default defineComponent({
  name: 'PageIndex',
  components: { Message },
  setup(){
    const form = ref(null)

    const state = reactive({
      alcool: null,
      gasolina: null,
      message: null,
      result: null
    })

    async function Calcular(){
      state.result = state.alcool / state.gasolina

      if(state.result <= 0.7){
        state.message = "Abasteça com Álcool !!"
      }else{
        state.message = "Abasteça com Gasolina !!"
      }
    }

    async function Reset(){
      state.alcool = null
      state.gasolina = null
      state.message = null
      state.result = null
    }

    return {
      form,
      state,
      Calcular,
      Reset
    }
  }
})
</script>
<style scoped>
  .input {
    max-width: 500px;
  }

  img {
    max-height: 120px;
  }
</style>
