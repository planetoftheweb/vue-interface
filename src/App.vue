<template>
  <div id="main-app" class="container">
    <div class="row justify-content-center">
      <add-appointment @add="addItem"/>
      <search-appointments/>
      <appointment-list :appointments="appointments" @remove="removeItem" @edit="editItem"/>
    </div>
  </div>
</template>

<script>
import AddAppointment from "./components/AddAppointment";
import SearchAppointments from "./components/SearchAppointments";
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
    AppointmentList,
    SearchAppointments,
    AddAppointment
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
    addItem: function(apt) {
      apt.aptId = this.aptIndex;
      this.aptIndex++;
      this.appointments.push(apt);
    },
    removeItem: function(apt) {
      this.appointments = _.without(this.appointments, apt);
    },
    editItem: function(id, field, text) {
      const aptIndex = _.findIndex(this.appointments, {
        aptId: id
      });
      this.appointments[aptIndex][field] = text;
    }
  }
};
</script>

