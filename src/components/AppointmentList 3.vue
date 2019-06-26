<template>
  <div>
    <div v-for="(item, i) in appointments" v-bind:key="i">
      <h4>{{item.petName}}</h4>
      <p>{{item.aptNotes}}</p>
    </div>
  </div>
</template>s

<script>
export default {
  name: "AppointmentList",
  props: ["appointments"]
};
</script>