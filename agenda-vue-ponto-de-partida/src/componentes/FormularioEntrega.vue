
<script setup>
import { ref } from 'vue'

const materia = ref('')
const tipo = ref('')
const data = ref('')
const enviarFormulario = defineEmits(['adicionar-entrega'])
</script>
<template>

<form @submit.prevent="adicionarEntrega">
<div>
    <label for="materia">Matéria</label>
    <input type="text" id="materia" v-model="materia" placeholder="Ex.: Matemática" required>
</div>
<div>
    <label for="tipo">Tipo</label>
    <select id="tipo" v-model="tipo" required>
        <option value="">Escolha o tipo</option>
        <option value="prova">Prova</option>
        <option value="trabalho">Trabalho</option>
        <option value="apresentacao">Apresentação</option>
    </select>
</div>
<div>
    <label for="data">Data</label>
    <input type="date" id="data" v-model="data" required>
</div>
<button type="submit">Adicionar</button>

</form>

</template>