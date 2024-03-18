<template>
  <component :is="sectionTag" :class="sectionClass">
    <div class="container">
      <div class="row justify-content-center">
        <div :class="columnClass">
          <h2 class="text-center h4 text-sans font-weight-normal text-uppercase text-brick-light bordered-title">
            {{ section.title }}
          </h2>
          <p class="text-center h5" v-if="section.body">
            {{ section.body }}
          </p>
        </div>
      </div>
      <div class="row flex-md-nowrap">

         <layout-room-teaser
           v-for="room in rooms"
           v-if="room.id!==currentNavItem.id && room.thumb"
           :key="'room-'+room.id"
           :room = "room"/>


      </div>
    </div>

  </component>
</template>

<script>

export default {
  name: "SectionLayoutRoomList",
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
    },
    columnClass () {
      return this.section.column || 'col-small'
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
