<template>
<h1>Events for Good!!</h1>
     <div class="events">
     <EventCard v-for="event in events" :key="event.id" :event="event"/>
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import axios from 'axios'

export default {
  name: "Home",
  components: {
    EventCard
  },
  data() {
    return {
      events: null
    }
  },
  created(){
    axios.get('https://my-json-server.typicode.com/V5NEXT/Vue-App/events')
    .then(response => {
      this.events = response.data
    })
    .catch(error => {
      console.log(error)
    })
  }
};
</script>
<style>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
