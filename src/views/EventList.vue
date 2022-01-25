<template>
  <div class="event">
      <h1>Events for good</h1>
    <img alt="Vue logo" src="../assets/logo.png" />
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import EventServices from '@/services/EventServices.js'

export default {
  name: "EventList",
  props: ['page'],
  components: {
    EventCard
  },
  data() {
    return {
      events: null
    }
  },
  created(){
    EventServices.getEvents(2, this.page)
      .then(response =>
        this.events = response.data)
      .catch(error =>
        console.log(error))
  }
};
</script>

<style scoped>
.event{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
