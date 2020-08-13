<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        Seleccione un tipo
        <v-select
          v-model="item"
          :items="items"
          return-object
        />
          
        <v-btn @click="addQuestion()">Añadir pregunta</v-btn>
      </v-col>


      <v-col cols="12" v-for="question in questions" :key="question.index">
       <component :is="question.component" />
      </v-col>

    </v-row>
  </v-container>
</template>

<script>

  import trueorfalse from './Questions/TrueOrFalse';
  import simple from './Questions/Simple';
  import multiple from './Questions/Multiple';
  import sentence from './Questions/Sentence';

  export default {
    name: 'Questions',

    data: () => ({
      items: [
        {
          text: 'Verdadero o falso',
          component: 'trueorfalse',
        },
        {
          text: 'Respuesta simple',
          component: 'simple',
        },
        {
          text: 'Respuesta multiple',
          component: 'multiple',
        },
        {
          text: 'Complete la frase',
          component: 'sentence',
        },
        
      ],
      item: {},
      questions: [ ],
      
    }),
    methods: {
      addQuestion() {
        let item = this.item;
        this.questions.push(item)
      }
    },
    components: {
      trueorfalse, simple, multiple, sentence
    },
  }
</script>
