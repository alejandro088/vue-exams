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
                    <v-radio label="Verdadero" value="true" />
                    <v-radio label="Falso" value="false" />
                </v-radio-group>
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
        }
    }
    
}
</script>