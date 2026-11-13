<script setup>
import { ref } from 'vue';

const props = defineProps({
    pendentes: Number,
    proxima: String
});

const emit = defineEmits(['adicionar-entrega', 'alternar-feita']);

const materia = ref('');
const tipo = ref('');
const data = ref('');
const tipoEscolhido = ref('todos');

const adicionarEntrega = () => {
    emit('adicionar-entrega', {
        materia: materia.value,
        tipo: tipo.value,
        data: data.value
    });
    materia.value = '';
    tipo.value = '';
    data.value = '';
};

const avancarEntrega = (entrega) => {
    emit('alternar-feita', entrega);
};
</script>

<template>
    <main class="principal">
        <section class="cartao resumo">
            <h2>Resumo</h2>

            <div class="indicadores">
                <p class="indicador">
                    <span class="rotulo">Pendentes</span>
                    <strong class="pendentes">{{ pendentes }}</strong>
                </p>

                <p class="indicador">
                    <span class="rotulo">Próxima entrega</span>
                    <strong class="proxima">{{ proxima }}</strong>
                </p>
            </div>
        </section>

        <section class="cartao nova-entrega">
            <form class="formulario" @submit.prevent="adicionarEntrega">
                <fieldset>
                    <legend>Nova entrega</legend>

                    <p>
                        <label for="materia">Matéria</label>
                        <input type="text" id="materia" class="campo-materia" v-model="materia" placeholder="Ex.: Matemática" required>
                    </p>

                    <p>
                        <label for="tipo">Tipo</label>
                        <select id="tipo" class="campo-tipo" v-model="tipo" required>
                            <option value="">Escolha o tipo</option>
                            <option value="prova">Prova</option>
                            <option value="trabalho">Trabalho</option>
                            <option value="apresentacao">Apresentação</option>
                        </select>
                    </p>

                    <p>
                        <label for="data">Data</label>
                        <input type="date" id="data" class="campo-data" v-model="data" required>
                    </p>

                    <button type="submit" class="botao-adicionar">Adicionar</button>
                </fieldset>
            </form>
        </section>

        <section class="cartao entregas">
            <h2>Próximas entregas</h2>

            <p class="filtro">
                <label for="filtro">Mostrar</label>
                <select id="filtro" class="campo-filtro" v-model="tipoEscolhido">
                    <option value="todos">Tudo</option>
                    <option value="prova">Só provas</option>
                    <option value="trabalho">Só trabalhos</option>
                    <option value="apresentacao">Só apresentações</option>
                </select>
            </p>
        </section>
    </main>
</template>