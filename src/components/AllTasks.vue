<script setup>
import { ref } from 'vue';

defineProps({
    flag: {
        type: Boolean,
        required: true,
    },
    TASKS: {
        type: Object,
        required: true,
    },
    switching: {
        type: Function,
        required: true,
    }
})



</script>

<template>
    <div class="contain" v-if="flag == false">
        <div class="contHead">
            <div class="titleTasks">TASKS</div>
            <button @click="switching" class="closeTasks"><p>x</p></button>
        </div>
        <div class="taskMassivCard">
            <div
            class="task"
            v-for="el in TASKS" :key="el.id">
                <div class="name">{{ el.title }}</div>
                <div class="buttonsTask">
                    <button class="info">info</button>
                    <button class="close">x</button>
                </div>
            </div>  
        </div>
    </div>
</template>

<style scoped>
    .contain {
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-direction: column;
        width: 80vw;
        height: 80vh;
        background: rgb(212, 211, 211);
        border-radius: 40px;
    }

    .contHead {
        position: relative;
        display: flex;
        width: 78vw;
        justify-content: center;
    }

    .closeTasks {
        right: 25px;
        top: 25px;
        position: absolute;
        border-radius: 100%;
        width: 30px;
        height: 30px;
        border: none;
        color: aliceblue;
        text-align: center;
        font-weight: 900;
        font-size: 24px;
        background: rgb(255, 135, 135);

    }
    .closeTasks p {
        position: absolute;
        top: -5px;
        right: 7px;
    }
    .titleTasks {
        text-align: center;
        padding-top: 20px;
        font-size: 24px;
        color: aliceblue;
        font-weight: 900;
    }
    .taskMassivCard {
        background-color: aqua;
        width: 70vw;
        height: 65vh;
        padding: 40px;
        display: grid;
        grid-template-columns: repeat(3, 33%);
    }
    .task {
        display: flex;
        justify-content: space-between;
        height: max-content;
        width: 10vw;
    }
</style>