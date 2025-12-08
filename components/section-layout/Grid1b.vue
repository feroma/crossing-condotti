<template>
  <component :is="sectionTag" :class="sectionClass">

    <div class="container">
      <div class="row">

        <div class="col-12 col-sm-4 d-flex flex-column">
          <picture-wrapper v-if="section.items[1].filename"
                           class="_mb-xs-gutter" :item="section.items[1]"></picture-wrapper>

          <div :class="section.items[1].class" v-else>
            <div :class="sentenceClasses.div">
              <div :class="sentenceClasses.text"
                   v-html="section.items[1].html"></div>
            </div>
          </div>


          <picture-wrapper v-if="section.items[2].filename"
                           class="mb-xs-gutter" :item="section.items[2]"></picture-wrapper>
          <div :class="section.items[2].class" v-else>
            <div :class="sentenceClasses.div">
              <div :class="sentenceClasses.text"
                   v-html="section.items[2].html"></div>
            </div>

          </div>


        </div>
        <div class="col-12 col-sm-8 mb-xs-gutter">
          <picture-wrapper :item="section.items[0]"></picture-wrapper>
        </div>

      </div>
    </div>

  </component>
</template>

<script>

export default {
  name: "SectionLayoutGrid1b",
  data () {
    return {
      show: false
    }
  },
  components: {},
  computed: {
    sectionClass () {
      let sectionClassDefault = ['section-layout-' + this.section.layout]
      let response = sectionClassDefault
      if (this.section.class) {
        response = [...sectionClassDefault, ...this.section.class]
      }
      return response.join(' ')
    },

    sectionTag () {
      return this.section.tag || 'section'
    }
  },
  methods: {},
  props: {
    section: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  }

}
</script>
<style>
</style>
