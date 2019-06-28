<template>
  <div class="col-12 col-md-10 col-lg-7">
    <div class="input-group my-3">
      <input
        id="SearchApts"
        placeholder="Search"
        type="text"
        class="form-control"
        aria-label="Search Appointments"
        v-model="searchTerm"
      >

      <div class="input-group-append">
        <button
          type="button"
          class="btn btn-primary dropdown-toggle"
          data-toggle="dropdown"
          aria-haspopup="true"
          aria-expanded="false"
        >
          Sort by
          <span class="caret"></span>
        </button>

        <div class="dropdown-menu dropdown-menu-right">
          <a href="#" class="dropdown-item d-flex justify-content-between" id="petName">
            Pet Name
            <font-awesome-icon icon="check"/>
          </a>

          <a class="dropdown-item d-flex justify-content-between" href="#" id="aptDate">
            Date
            <font-awesome-icon icon="check"/>
          </a>

          <a href="#" class="dropdown-item d-flex justify-content-between" id="ownerName">
            Owner
            <font-awesome-icon icon="check"/>
          </a>

          <div class="dropdown-divider" role="separator"></div>

          <a class="dropdown-item d-flex justify-content-between" href="#" id="asc">
            Asc
            <font-awesome-icon icon="check"/>
          </a>

          <a class="dropdown-item d-flex justify-content-between" href="#" id="desc">
            Desc
            <font-awesome-icon icon="check"/>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
export default {
  name: "SearchAppointments",
  data() {
    return {
      searchTerm: ""
    };
  },
  watch: {
    searchTerm: function() {
      this.$emit("searchRecords", this.searchTerm);
    }
  },
  components: {
    FontAwesomeIcon
  }
};
</script>
