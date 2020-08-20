<template>
    <v-container>
        <v-row>
            <v-col cols="6">
                <v-textarea
                label="Escriba su pregunta.."
                :value="message"
                auto-grow
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
             <v-col cols="6">
                <h3>{{ message }}</h3>
                <v-checkbox v-for="answer in answers"  
                    :value="answer.request"
                    :key="answer.text"
                    :color="answer.color" 
                >
                    <template v-slot:label>
                        <div><strong :class="`${answer.color}--text`">{{answer.text}}</strong></div>
                    </template>
                </v-checkbox>
                <v-btn @click="validate()">Corregir!!</v-btn>
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
                request: false,
                color: 'default',
            },
        }
    },
    methods: {
      addAnswer() {
        
        this.answers.push({
            text: this.item.text,
            correct: this.item.correct,
            request: this.item.request,
            color: this.item.color,
        })
      },
      validate() {
        
        let answers = this.answers
        answers = answers.forEach( (answer) => {
           if (answer.correct != answer.request)
           {
               answer.color = 'error'
           } else {
               answer.color = 'success'
           }

        this.answers = answers;

        })
      }
    },
}
</script>