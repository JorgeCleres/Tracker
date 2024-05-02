<template>
    <main class="columns is-gapless in-multile">
        <div class="column is-one-quarter">
            <barra-lateral />
        </div>

        <div class="column is-three-quarter conteudo">
            <formulario @aoSalvarTarefa="salvarTarefa"/>
            <div class="lista">
                <tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
                <box v-if="listaEstaVazia">Você não está muito produtivo hoje :(</box>
            </div>
        </div>
    </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Box from './components/Box.vue';
import Formulario from './components/Formulario.vue';
import Tarefa from './components/Tarefa.vue';
import ITarefa from './interfaces/ITarefa';

export default defineComponent({
  components: { BarraLateral, Formulario, Tarefa, Box },
    name: 'App',
    data() {
        return {
            tarefas: [] as ITarefa[]
        }
    },
    computed: {
        listaEstaVazia(): boolean {
            return this.tarefas.length === 0
        }
    },
    methods: {
        salvarTarefa(tarefa: ITarefa) {
            this.tarefas.push(tarefa)
        }
    }
});
</script>

<style>
    .lista {
        padding: 1.25rem;
    }
</style>
