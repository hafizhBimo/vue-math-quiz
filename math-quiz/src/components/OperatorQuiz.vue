<template>
    <div>
        <div v-if="isStarted">
            <h4>{{ operandLeft }} {{ operator }} {{ operandRight }}</h4>
            <button @click="selectAnswer(answer)" v-for="answer, index of answers" :key="index">{{ answer }}</button>
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
            operandRight: null,
            answers: [],
            expectedAnswer: null
        }
    },
    methods: {
        startQuiz() {
            this.isStarted = true
            this.operandLeft = parseInt(Math.random() * 13)
            this.operandRight = parseInt(Math.random() * 13)
            const methods = {
                "+": (a, b) => a + b,
                "-": (a, b) => a - b,
                "/": (a, b) => a / b,
                "*": (a, b) => a * b
            }
            const methodToUse = methods[this.operator]
            this.answers = []
            for (let i = 0; i < 5; i++) {
                const answer = methodToUse(parseInt(Math.random() * 13), parseInt(Math.random() * 13))
                this.answers.push(answer)
            }
            const expectedAnswer = methodToUse(this.operandLeft, this.operandRight)
            this.answers[parseInt(Math.random() * this.answers.length)] = expectedAnswer
            this.expectedAnswer = expectedAnswer
        },
        selectAnswer(answerSelected) {
            if (answerSelected !== this.expectedAnswer) {
                alert('WRONG ANSWER')
            }
            this.startQuiz()
        }
    }
}
</script>