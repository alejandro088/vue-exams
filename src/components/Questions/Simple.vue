<template>
    <v-container>
        <v-row>
            <v-col cols="12">
                <v-textarea
                label="Escriba su pregunta.."
                :value="message"
                >

                </v-textarea>

                <v-radio-group v-model="correct">
                    <v-radio v-for="answer in answers"  
                        :value="answer" 
                        :label="answer"
                        :key="answer" 
                    >
                    
                    </v-radio>
                </v-radio-group>
                <v-text-field v-model="item" label="Escriba una respuesta.."></v-text-field>
                <v-btn @click="addAnswer()">Añadir respuesta</v-btn>
            </v-col>
        </v-row>
     </v-container>
</template>
    
<script>
export default {
    data() {
        return {
            message: '',
            answers: [],
            correct: '',
            item: '',
        }
    },
    methods: {
      addAnswer() {
        let item = this.item;
        this.answers.push(item)
      }
    },
}
</script>