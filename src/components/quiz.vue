<template>
    <v-tabs
            dark
            color="indigo"
            show-arrows
    >
        <v-tabs-slider color="white"></v-tabs-slider>

        <v-tab
                v-for="(item, index) in checkboxes"
                :key="index"
                :href="'#tab-' + index"
        >
            {{ index }}
        </v-tab>

        <v-btn color="blue" @click="saveAnswers">Сохранить</v-btn>

        <v-tabs-items>
            <v-tab-item
                    v-for="(item, index) in checkboxes"
                    :key="index"
                    :value="'tab-' + index"
            >
                <v-card flat>
                    <v-card-text>
                        <p class="checkbox-question">{{ item.question }}</p>
                        <v-container fluid>
                            <v-radio-group v-model="item.checked" :mandatory="false">
                                <v-radio v-for="(answer, secondIndex) in item.answers" :key="secondIndex"
                                         :label="answer" :value="answer"></v-radio>
                            </v-radio-group>
                        </v-container>
                    </v-card-text>
                </v-card>
            </v-tab-item>
        </v-tabs-items>
    </v-tabs>
</template>

<script>
  import _ from 'lodash'
  import jsPDF from 'jspdf'

  export default {
    props: ['checklist'],
    data() {
      return {
        checkboxes: []
      }
    },
    created() {
      this.checkboxes = _.cloneDeep(this.checklist)
    },
    methods: {
      saveAnswers() {
        const doc = new jsPDF()
        let output = ''

        this.checkboxes.forEach((checkbox, index) => {
          output += `${index}) ${checkbox.question}`
          output += checkbox.checked ? ` ${checkbox.checked} ` : 'Нет ответа'
        })
        doc.text(output, 10, 10)
        doc.save('чек-лист-безопасное-вождение.pdf')
      }
    }
  }
</script>

<style lang="stylus">
    .checkbox-question
        font-size 16px
        margin 0
</style>
