<template>
  <div id="main-app" class="container">
    <div class="row justify-content-center">
      <appointment-list :appointments="appointments" @remove="removeItem"/>
    </div>
  </div>
</template>

<script>
import AppointmentList from "./components/AppointmentList";
import _ from "lodash";
import axios from "axios";

export default {
  name: "MainApp",
  data: function() {
    return {
      appointments: [],
      aptIndex: 0
    };
  },
  components: {
    AppointmentList
  },
  mounted() {
    axios.get("./data/appointments.json").then(
      response =>
        (this.appointments = response.data.map(item => {
          item.aptId = this.aptIndex;
          this.aptIndex++;
          return item;
        }))
    );
  },
  methods: {
    removeItem: function(apt) {
      this.appointments = _.without(this.appointments, apt);
    }
  }
};
</script>

