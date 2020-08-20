<template>
    <v-container>
        <v-row>
            <v-col cols="8">
                <v-textarea
                label="Escriba [...] por cada palabra que el usuario deba completar en su frase"
                v-model="message"
                >

                </v-textarea>
                <v-btn @click="addAnswer()">Añadir respuestas</v-btn>
               
                <v-text-field v-for="answer in answers" v-model="answer.text" :key="answer.index" label="Escriba una respuesta.."></v-text-field>
            </v-col>
             <v-col cols="4">
                <pre>{{ $data }}</pre>
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
            }
        }
    },
    methods: {
        addAnswer: function() {
            let count = this.message.match(new RegExp(/\[([A-Za-z])\w+\]/, 'g'));
            console.log(count)

            this.answers = []

            for (let i = 0; i < count; i++) {
                this.answers.push({text: this.item.text});
                
            }
        }
    },
}
</script>