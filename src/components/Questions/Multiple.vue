<template>
    <v-container>
        <v-row>
            <v-col cols="12">
                <v-textarea
                label="Escriba su pregunta.."
                :value="message"
                >

                </v-textarea>

                
                <v-checkbox v-for="answer in answers"  
                    :value="answer.correct" 
                    :label="answer.text"
                    :key="answer.text" 
                >
                
                </v-checkbox>
               
                <v-text-field v-model="item.text" label="Escriba una respuesta.."></v-text-field>
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
            item: {
                text: '',
                correct: false,
            },
        }
    },
    methods: {
      addAnswer() {
        
        this.answers.push({
            text: this.item.text,
            correct: this.item.correct
        })
      }
    },
}
</script>