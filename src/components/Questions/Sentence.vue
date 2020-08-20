<template>
    <v-container>
        <v-row>
            <v-col cols="6">
                <p>Encierre entre corchetes, cada palabra que el estudiante completará en su frase. Luego haga click en Validar</p>
                <v-textarea
                    label="Encierre entre corchetes, cada palabra que el estudiante completará en su frase"
                    v-model="message"
                    rows="1"
                    auto-grow
                />

                <v-btn @click="addAnswer()">Validar</v-btn>

                <pre>{{ $data }}</pre>
               
                
            </v-col>
            <v-col cols="6">
                <form id="phrase">
                    <p v-html="phrase"></p>
                    <v-btn v-on:click.prevent="validate">Corregir!!</v-btn>
                </form>

                <p v-for="result in results" :key="result.index">{{ result }}</p>
                
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
            results: [],
        }
    },
    methods: {
        addAnswer: function() {
            let answers = this.message.match(new RegExp(/\[([A-Za-z])\w+\]/, 'g'));
            console.log(answers)

            this.answers = answers

        },
        validate() {               
           
           let answers = this.answers
           let results = []
           let inputs = document.getElementById("phrase").getElementsByTagName("input");

           inputs.forEach((element, index) => {
               
                let answer = answers[index].replace("[","").replace("]","")

                if (answer === element.value){
                    console.log(answer, element.value, true)
                    results[index] = "La palabra "+element.value+" es correcta"     
                } else {
                    console.log(answer, element.value, false)
                    results[index] = "La palabra "+element.value+" es incorrecta"
                }
           });

           this.results = results;

           
        }
    },
    computed: {
        phrase: function() {
            let result = this.message.replace(new RegExp(/\[([A-Za-z])\w+\]/, 'g'), "<input type='text' placeholder='......'></input>")
            return result;
        }
    }
}
</script>