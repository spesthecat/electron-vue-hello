<template>
    <div id='todo-modal'>
        <div :class="{ 'hi-show': show, 'hi': true} ">
            <div class='brief'>
                {{ todo.brief }}
            </div>
            <div class='long'>
                {{ todo.details }}
            </div>

        </div>
        <div :class="{ 'modal-background-show': show, 'modal-background': true }" @click.prevent="$store.commit('todoModal/hideModal')"/>
    </div>
</template>

<script>

import { mapState, mapMutations } from 'vuex';

export default {
    name: 'TodoModal',
    computed: {
        ...mapState('todoModal', {
            show: state => state.show,
            todo: state => state.todo.item,
        })
    },
    methods: {
        ...mapMutations([
            'todoModal/hideModal'
        ])
    }
}

</script>

<style scoped>

.brief {

}

.long {

}

.hi {
    position: absolute;
    transition: transform 0.1s ease;
    transform: scale(0, 0);
    height: 70%;
    width: 60%;
    flex: 2 1 auto;
    background-color: white;
    border-radius: 10px;
    z-index: 2; 
}

.hi-show {
    transform: scale(1);
}

#todo-modal {
    position: absolute;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.modal-background {
    color: white;
    pointer-events: none;
    position: absolute;
    transition: opacity 0.1s ease;
    width: 100%;
    height: 100%;
    background-color: #000;
    opacity: 0;
    z-index: 1;
}

.modal-background-show {
    pointer-events: auto;
    opacity: 0.85;
}

</style>