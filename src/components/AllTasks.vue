<script setup>
import { ref, computed } from 'vue';

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

const delTask = computed((name) => {
    localStorage.removeItem(name)
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
                <div class="info">
                    {{ el.taskBody }}
                    <button class="delete" @click="delTask(el.id)">delete</button>
                </div>
            </div> 
        </div>
    </div>
</template>

<style scoped>
    .delete {
        border: none;
        
        position: absolute;
        right: 20px;
        top: 20px;
        color: rgb(69, 74, 69);
        font-size: 20px;
        font-weight: 900;
        padding: 5px;
        border-radius: 20px;
        transition: all .2s ease;
    }
    .delete:hover {
        color: rgb(180, 24, 24);
        background-color: rgb(200, 200, 200);
    }
    .name {
        display: flex;
        align-items: center;
        font-size: 20px;
        text-align: center;
        padding: 10px;
        color: rgb(70, 65, 59);
        font-weight: 900;
        
    }
    .task {
        border-radius: 50px;
        height: 5em;
        display: flex;
        justify-content: space-between;
        width: 100%;
        background: rgb(244, 194, 194);
        position: relative;
    }
    .info {
        font-size: 16px;
        padding: 5px 40px;
        width: 50vw;
        border: none;
        min-height: 5em;
        border-radius: 50px;
        color: aliceblue;
        background: rgb(233, 126, 126);
        margin-right: 15px;
        position: absolute;
        right: -15px;
    }
    .contain {
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-direction: column;
        width: 80vw;
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
        width: 70vw;
        min-height: 65vh;
        padding: 40px;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 16px;
    }
</style>