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
                        <v-radio label="Verdadero" value="Verdadero" />
                        <v-radio label="Falso" value="Falso" />
                    </v-radio-group>
                    
                    <v-col cols="12">
                        <pre>{{ $data }}</pre>
                    </v-col>
                </v-row>
            </v-col>
            <v-col cols="6">
                 <h3>{{ message }}</h3>
                 <v-radio-group v-model="request">
                    <v-radio label="Verdadero" value="Verdadero" />
                    <v-radio label="Falso" value="Falso" />
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
            correct: true,
            request: false,
            color: 'default',
            response: '',
        }
    },
    methods: {
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