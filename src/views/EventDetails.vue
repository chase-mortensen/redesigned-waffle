<template>
  <section v-if="event">
    <h1>{{ event?.title }}</h1>
    <p>{{ event?.time }} on {{ event?.date }} @ {{ event?.location }}</p>
    <p>{{ event?.description }}</p>
  </section>
</template>

<script>
import EventService from '@/services/EventService'

export default {

  created() {
    EventService.getEvent(this.id)
      .then(response => {
        this.event = response.data
      })
      .catch(error => {
        console.log(error)
      })
  },

  data() {
    return {
      event: null
    }
  },

  props: {
    id: {
      required: true
    }
  }

}
</script>