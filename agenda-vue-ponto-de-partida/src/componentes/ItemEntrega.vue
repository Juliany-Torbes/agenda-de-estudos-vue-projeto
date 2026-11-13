
<script setup>

defineProps({
    dados: Array
});
const emit = defineEmits(['apagar', 'alternar-feita']);

import {
    formatarData,
    nomearTipo,

} from './agenda.js';

</script>
<template>
    <div>
        <ul>
            <li v-for="dado in dados" :key="dado.id">
                <strong>{{ dado.materia }}</strong> - Data: {{ formatarData(dado.data) }} - Tipo: {{ nomearTipo(dado.tipo) }} - Feita: {{ dado.feita ? 'Sim' : 'Não' }}
                <span>{{ dado.descricao }} - R$ {{ dado.valor.toFixed(2) }} ({{ dado.categoria }})</span>
            </li>
        </ul>
        <button @click="$emit('apagar', pendente)">Atividade pendente</button>
        <button @click="$emit('alternar-feita', proxima)">Próxima atividade</button>

    </div>
</template>