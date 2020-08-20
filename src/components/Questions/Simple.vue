<template>
    <v-container>
        <v-row>
            <v-col cols="6">
                <v-row justify="space-around">
                    <v-col cols="12">
                        <v-textarea
                            label="Escriba su pregunta.."
                            v-model="message"
                            rows="1"
                            auto-grow
                        >

                        </v-textarea>
                    </v-col>

                    <v-radio-group v-model="correct">
                        <v-radio v-for="answer in answers"  
                            :value="answer" 
                            :label="answer"
                            :key="answer" 
                        >
                        
                        </v-radio>
                
                    </v-radio-group>
                    <v-col cols="12">
                        <v-text-field v-model="item" label="Escriba una respuesta.."></v-text-field>
                        <v-btn @click="addAnswer()">Añadir respuesta</v-btn>
                        <pre>{{ $data }}</pre>
                    </v-col>
                </v-row>
            </v-col>
             <v-col cols="6">
                <h3>{{ message }}</h3>
                <v-radio-group v-model="request">
                    <v-radio v-for="answer in answers"  
                        :value="answer" 
                        :label="answer"
                        :key="answer" 
                    >
                    
                    </v-radio>
                
                </v-radio-group>
                
                <div><strong :class="`${color}--text`">{{response}}</strong></div>
                        
                
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
            correct: '',
            item: '',
            color: 'default',
            response: '',
            request: '',
        }
    },
    methods: {
      addAnswer() {
        let item = this.item;
        this.answers.push(item)
      },
      validate() {
        
        
           if (this.correct != this.request)
           {
               this.color = 'error'
               this.response = `Su respuesta es incorrecta. La respuesta correcta era ${this.correct}`
           } else {
               this.color = 'success'
               this.response = 'Su respuesta es correcta'
           }

    
      }
    },
}
</script>