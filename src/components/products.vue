<template>
  <div>
    <div class="row">
      <div class="col-sm-6">
        <childCom1 />
      </div>
      <div class="col-sm-6">
        <childCom2 />
      </div>
    </div>
  </div>
</template>

<script>
import childCom1 from "./childCom1.vue";
import childCom2 from "./childCom2.vue";
export default {
  components: {
    childCom1,
    childCom2,
  },
};
</script>

<style></style>
