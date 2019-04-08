<template>
<v-tabs
        dark
        color="indigo"
        show-arrows
>
    <v-tabs-slider color="white"></v-tabs-slider>

    <v-tab
            v-for="(item, index) in checklist"
            :key="index"
            :href="'#tab-' + index"
    >
        {{ index }}
    </v-tab>

    <v-tabs-items>
        <v-tab-item
                v-for="(item, index) in checklist"
                :key="index"
                :value="'tab-' + index"
        >
            <v-card flat>
                <v-card-text>{{ item.question }}</v-card-text>
            </v-card>
        </v-tab-item>
    </v-tabs-items>
</v-tabs>
</template>

<script>
export default {
  props: ['checklist'],
  data () {
    return {}
  },
}
</script>
