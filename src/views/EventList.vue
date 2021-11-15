<template>
  <div>
    <h1>Events Listing: View Here</h1>
    <EventCard
      v-for="event in events"
      :key="event.id"
      :event="event"
    ></EventCard>
    <BaseIcon />
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService.js'

export default {
  components: {
    EventCard,
  },
  created() {
    EventService.getEvents() // Does a get request
      .then((response) => {
        this.events = response.data
      })
      .catch((error) => {
        console.log('There was an error:', error.response) // Logs out the error
      })
  },
  data() {
    return {
      events: [],
    }
  },
}
</script>
