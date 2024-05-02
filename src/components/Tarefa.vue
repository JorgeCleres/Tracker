<template>
    <box>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descricao'}}
            </div>
            <div class="column">
                <cronomotro :tempo-em-segundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </box>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import Cronomotro from './Cronomotro.vue'
import ITarefa from '@/interfaces/ITarefa';
import Box from './Box.vue';

export default defineComponent({
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Tarefa',
    components: { Cronomotro, Box },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true,
        }
    }

})
</script>