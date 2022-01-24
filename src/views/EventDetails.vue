<template>
  <div v-if="event">
      <h1>{{ event.title}}</h1>
      <p>{{event.time}} at {{event.date}} @ {{event.place}}</p>
      <p>{{event.description}}</p>
  </div>
</template>

<script>
import EventServices from '@/services/EventServices.js'
export default {
    props: ['id'],
    data(){
        return{
            event: null
        }
    },
    created(){
        EventServices.getEvent(this.id)
      .then(response =>
        this.event = response.data)
      .catch(error =>
        console.log(error))
    }

}
</script>

<style>

</style>