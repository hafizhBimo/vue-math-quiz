<template>
    <div>
        <div v-if="isStarted">
            <h4>{{ operandLeft }} {{ operator }} {{ operandRight }}</h4>
        </div>
        <button @click="$emit('onBack')">back</button>
        <button @click="startQuiz">Start quiz!</button>
    </div>
</template>

<script>
export default {
    props: ['operator'],
    data() {
        return {
            isStarted: false,
            operandLeft: null,
            operandRight: null
        }
    },
    methods: {
        startQuiz() {
            this.isStarted = true
            this.operandLeft = parseInt(Math.random() * 13)
            this.operandRight = parseInt(Math.random() * 13)
        }
    }
}
</script>