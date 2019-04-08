<template>
    <quiz :checklist="checklist"></quiz>
</template>

<script>
import checklist from '@/checklists/first.json'
import quiz from '@/components/quiz'

export default {
  components: {
    quiz
  },
  data () {
    return {
      checklist: []
    }
  },
  created() {
    this.checklist = checklist
  }
}
</script>
