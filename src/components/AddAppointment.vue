<template>
  <div class="col-12">
    <div class="card textcenter mt-3">
      <div class="card-header bg-primary text-white" @click="hidepanel=!hidepanel">
        <font-awesome-icon icon="plus" class="mr-3"/>Add Appointment
      </div>

      <div class="card-body" :class="{ 'd-none': hidepanel}">
        <form id="aptForm" @submit.prevent="requestAdd">
          <div class="form-group form-row">
            <label class="col-md-2 col-form-label text-md-right" for="petName">Pet Name</label>
            <div class="col-md-10">
              <input
                type="text"
                class="form-control"
                name="petName"
                id="petName"
                placeholder="Pet's Name"
                v-model="formData.petName"
              >
            </div>
          </div>

          <div class="form-group form-row">
            <label class="col-md-2 col-form-label text-md-right" for="ownerName">Pet Owner</label>
            <div class="col-md-10">
              <input
                type="text"
                class="form-control"
                id="ownerName"
                placeholder="Owner's Name"
                v-model="formData.ownerName"
              >
            </div>
          </div>

          <div class="form-group form-row">
            <label class="col-md-2 col-form-label text-md-right" for="aptDate">Date</label>
            <div class="col-md-4">
              <input type="date" class="form-control" id="aptDate" v-model="formData.aptDate">
            </div>
            <label class="col-md-2 col-form-label text-md-right" for="aptTime">Time</label>
            <div class="col-md-4">
              <input
                type="time"
                class="form-control"
                name="aptTime"
                id="aptTime"
                v-model="formData.aptTime"
              >
            </div>
          </div>

          <div class="form-group form-row">
            <label class="col-md-2 text-md-right" for="aptNotes">Apt. Notes</label>
            <div class="col-md-10">
              <textarea
                class="form-control"
                rows="4"
                cols="50"
                name="aptNotes"
                id="aptNotes"
                placeholder="Appointment Notes"
                v-model="formData.aptNotes"
              ></textarea>
            </div>
          </div>

          <div class="form-group form-row mb-0">
            <div class="offset-md-2 col-md-10">
              <button type="submit" class="btn btn-primary d-block ml-auto">Add Appointment</button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
export default {
  name: "AddAppointment",
  data() {
    return {
      formData: [],
      hidepanel: true
    };
  },
  components: {
    FontAwesomeIcon
  },
  methods: {
    requestAdd: function() {
      this.formData = {
        petName: this.formData.petName,
        petOwner: this.formData.ownerName,
        aptDate: this.formData.aptDate + " " + this.formData.aptTime,
        aptNotes: this.formData.aptNotes
      };
      this.$emit("add", this.formData);
      this.formData = [];
      this.hidepanel = true;
    }
  }
};
</script>
<style>
.card-header {
  cursor: pointer;
}
</style>
