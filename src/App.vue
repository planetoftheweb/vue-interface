<template>
  <div id="main-app" class="container">
    <h4>{{title}}</h4>
    <font-awesome-icon icon="plus" class="mr-2"/>Add Appointment
    <div v-for="(item, i) in appointments" v-bind:key="i">
      <h4>{{item.petName}}</h4>
      <p>{{item.aptNotes}}</p>
    </div>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

export default {
  name: "MainApp",
  data: function() {
    return {
      title: "Appointment List",
      appointments: [
        {
          petName: "Spot",
          petOwner: "Constance Smith",
          aptDate: "2017-07-24 08:30",
          aptNotes: "This German Shepherd is having some back pain"
        },
        {
          petName: "Goldie",
          petOwner: "Barot Bellingham",
          aptDate: "2017-07-22 15:50",
          aptNotes: "This Goldfish has some weird spots in the belly"
        },
        {
          petName: "Mitten",
          petOwner: "Hillary Goldwyn",
          aptDate: "2017-07-21 9:15",
          aptNotes: "Cat has excessive hairballs"
        },
        {
          petName: "Buffy",
          petOwner: "Hassum Harrod",
          aptDate: "2017-07-20 15:30",
          aptNotes:
            "This Chihuahua has not eaten for three days and is lethargic"
        }
      ]
    };
  },
  components: {
    FontAwesomeIcon
  }
};
</script>

