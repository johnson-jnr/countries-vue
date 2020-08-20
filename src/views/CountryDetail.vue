<template>
  <div class="details">
    <SingleCountry :name="country" />
  </div>
</template>

<script>
// @ is an alias to /src
import SingleCountry from "@/components/SingleCountry.vue";

export default {
  name: "CountryDetail",
  props: ["country"],

  data() {
    return {};
  },
  components: {
    SingleCountry,
  },
};
</script>
<style >
.details {
  padding-top: 30px;
  background-color: whitesmoke;
}
</style>
